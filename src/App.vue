<template>
  <div class="card">
    <DataTable
      :value="products"
      resizableColumns
      columnResizeMode="expand"
      showGridlines
      tableStyle="min-width: 50rem"
      @resize="handleColumnGroupResize"
    >
      <ColumnGroup type="header">
        <Row>
          <Column header="test" :colspan="1"> </Column>
          <Column header="test1" :colspan="3"> </Column>
        </Row>
      </ColumnGroup>
      <Column field="code" header="Code"></Column>
      <Column field="name" header="Name"></Column>
      <Column field="category" header="Category"></Column>
      <Column field="quantity" header="Quantity"></Column>
    </DataTable>
  </div>
</template>

<script>
import { ProductService } from '@/service/ProductService';
export default {
  data() {
    return {
      products: null,
    };
  },
  methods: {
    handleColumnGroupResize(event) {
      const groupHeader = event.target.querySelector('.p-column-group-header');
      const groupColumns = event.target.querySelectorAll(
        '.p-column-group-child'
      );
      const groupWidth = groupHeader.offsetWidth;

      const columnWidth = groupWidth / groupColumns.length;
      groupColumns.forEach((column) => {
        column.style.width = columnWidth + 'px';
      });
    },
  },
  mounted() {
    ProductService.getProductsMini().then((data) => (this.products = data));
  },
};
</script>
