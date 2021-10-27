<!--  -->

<template>
  <div>
    <div class="custom-table">
      <div class="custom-table--fixed-wrapper">
        <div class="custom-table--header-wrapper">
          <table class="table table-bordered">
            <tr>
              <th>Game ID</th>
            </tr>
          </table>
        </div>

        <div class="custom-table--body-wrapper is-fixed" style="height: 300px">
          <table class="table table-hover table-bordered">
            <tr>
              <td>1</td>
            </tr>
            <tr>
              <td>2</td>
            </tr>
            <tr>
              <td>13</td>
            </tr>
            <tr>
              <td>1</td>
            </tr>
            <tr>
              <td>2</td>
            </tr>
            <tr>
              <td>13</td>
            </tr>
            <tr>
              <td>1</td>
            </tr>
            <tr>
              <td>2</td>
            </tr>
            <tr>
              <td>13</td>
            </tr>
            <tr>
              <td>1</td>
            </tr>
            <tr>
              <td>2</td>
            </tr>
            <tr>
              <td>13</td>
            </tr>
            <tr class="gutter"></tr>
          </table>
        </div>
      </div>
      <div class="middle-table-wrapper custom-table--header-wrapper">
        <table class="table table-bordered">
          <tr>
            <th>Game ID</th>
            <th>Status</th>
            <th>Players</th>
            <th>Turn</th>
            <th>Last Turn</th>
            <th>Operations</th>
            <th class="gutter"></th>
          </tr>
        </table>
      </div>
      <div
        class="bottom-table-wrapper custom-table--body-wrapper"
        style="height: 300px"
      >
        <table class="table table-hover table-bordered">
          <tr>
            <td>1</td>
            <td>IN PROGRESS</td>
            <td>4/4</td>
            <td>tedbeem</td>
            <td>11/12/13 6:30 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>2</td>
            <td>RECRUITING</td>
            <td>4/5</td>
            <td>N/A</td>
            <td>11/12/13 3:10 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>13</td>
            <td>IN PROGRESS</td>
            <td>3/3</td>
            <td>D-Halt-on</td>
            <td>11/12/13 9:00 AM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>1</td>
            <td>IN PROGRESS</td>
            <td>4/4</td>
            <td>tedbeem</td>
            <td>11/12/13 6:30 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>2</td>
            <td>RECRUITING</td>
            <td>4/5</td>
            <td>N/A</td>
            <td>11/12/13 3:10 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>13</td>
            <td>IN PROGRESS</td>
            <td>3/3</td>
            <td>D-Halt-on</td>
            <td>11/12/13 9:00 AM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>1</td>
            <td>IN PROGRESS</td>
            <td>4/4</td>
            <td>tedbeem</td>
            <td>11/12/13 6:30 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>2</td>
            <td>RECRUITING</td>
            <td>4/5</td>
            <td>N/A</td>
            <td>11/12/13 3:10 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>13</td>
            <td>IN PROGRESS</td>
            <td>3/3</td>
            <td>D-Halt-on</td>
            <td>11/12/13 9:00 AM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>1</td>
            <td>IN PROGRESS</td>
            <td>4/4</td>
            <td>tedbeem</td>
            <td>11/12/13 6:30 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>2</td>
            <td>RECRUITING</td>
            <td>4/5</td>
            <td>N/A</td>
            <td>11/12/13 3:10 PM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
          <tr>
            <td>13</td>
            <td>IN PROGRESS</td>
            <td>3/3</td>
            <td>D-Halt-on</td>
            <td>11/12/13 9:00 AM</td>
            <td><button class="btn btn-primary">View</button></td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import $ from "jquery";
$;
export default {
  name: "",
  components: {},
  data() {
    return {};
  },

  watch: {},

  computed: {},

  mounted() {
    this.initScroll();
    this.initHover();
  },

  methods: {
    initScroll() {
      // 同步两边的滚动
      $(".custom-table--body-wrapper").on("scroll", function () {
        // var scrollHeight = $(this).prop("scrollHeight");
        // var scrollWidth = $(this).prop("scrollWidth");
        var scrollTop = $(this).prop("scrollTop");
        var scrollLeft = $(this).prop("scrollLeft");
        console.log(scrollTop, scrollLeft);
        $(".middle-table-wrapper").prop("scrollLeft", scrollLeft);
        $(".custom-table--body-wrapper.is-fixed").prop("scrollTop", scrollTop);
      });
    },

    initHover() {
      let getRowIndex = function (event) {
        let target = event.target;
        if (target.tagName === "TR") {
          return $(target).index();
        } else {
          return $(event.target).parent("tr").index();
        }
      };

      // 同步两边的 hover 效果
      $(".custom-table--body-wrapper tr").hover(
        function (event) {
          let index = getRowIndex(event);
          $(
            ".custom-table--body-wrapper tr:nth-child(" + (index + 1) + ")"
          ).addClass("hover");
        },
        function (event) {
          let index = getRowIndex(event);
          $(
            ".custom-table--body-wrapper tr:nth-child(" + (index + 1) + ")"
          ).removeClass("hover");
        }
      );
    },
  },
};
</script>

<style lang="css" scoped>
.custom-table {
  position: relative;
}

/** 右侧边框 */
.custom-table::before {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  border-right: 1px solid #ddd;
}

/** 底部边框 */
.custom-table::after {
  content: "";
  display: block;
  height: 0px;
  position: relative;
  top: -1px;
  border-bottom: 1px solid #ddd;
}

.custom-table .table {
  table-layout: fixed;
  margin-bottom: 0;
}

.custom-table--body-wrapper {
  overflow: auto;
  margin-top: -1px;
}

/** Header 右侧的空隙,这个宽度需要在不同操作系统进行计算 */
.custom-table th.gutter {
  width: 16px;
  padding: 0 !important;
}

.custom-table--body-wrapper.is-fixed {
  overflow-y: hidden;
}

.custom-table--header-wrapper {
  overflow: hidden;
}

.custom-table--fixed-wrapper {
  box-shadow: 4px 0px 4px rgba(0, 0, 0, 0.1);
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 131px;
  background-color: #fff;
}

.custom-table td,
.custom-table th {
  white-space: nowrap;
  overflow: hidden;
  height: 42px;
  padding: 2px !important;
}

.custom-table tbody > tr.hover > td {
  background-color: #b32626;
}

.bottom-table-wrapper table td {
  width: 130px;
}

.custom-table--header-wrapper table th {
  width: 130px;
}

th,
td {
  border-right: 1px solid #ccc;
}
</style>
