<template>
    <div class="card">
        <DataTable
            :value="products"
            resizableColumns
            columnResizeMode="expand"
            showGridlines
            tableStyle="min-width: 50rem"
        >
            <ColumnGroup type="header">
                <Row>
                    <Column
                        header="Head1"
                        :colspan="1"
                    >
                    </Column>
                    <Column
                        header="Head2"
                        :colspan="3"
                    >
                    </Column>
                </Row>
                <Row>
                    <Column header="Code"> </Column>
                    <Column header="Name"> </Column>
                    <Column header="Category"></Column>
                    <Column header="Quantity"></Column>
                </Row>
            </ColumnGroup>
            <Column
                field="code"
                header="Code1"
            ></Column>
            <Column
                field="name"
                header="Name1"
            ></Column>
            <Column
                field="category"
                header="Category1"
            ></Column>
            <Column
                field="quantity"
                header="Quantity1"
            ></Column>
        </DataTable>
    </div>
</template>
<script>
import { ProductService } from "@/service/ProductService";
export default {
    data() {
        return {
            products: null,
        };
    },
    mounted() {
        ProductService.getProductsMini().then((data) => (this.products = data));
    },
};
</script>

<style>
.dot-icon {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: black;
    margin-right: 5px;
    cursor: col-resize;
}

.header-content {
    display: flex;
    align-items: center;
}

.header-text {
    margin-right: 5px;
}

.right {
    margin-left: auto;
}
</style>
