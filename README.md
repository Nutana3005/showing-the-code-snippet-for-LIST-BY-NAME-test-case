# showing-the-code-snippet-for-LIST-BY-NAME-test-case
def test_list_products_by_name(self):
    # Create products with unique names
    product1 = Product(name="ToyCar", category="Toys", available=True)
    product2 = Product(name="ToyTrain", category="Toys", available=True)
    product1.save()
    product2.save()
    
    # Send a request to list products by name
    response = self.client.get("/products?name=ToyCar")
    
    # Assert the response contains only products with the specified name
    assert response.status_code == 200
    assert len(response.json) == 1
    assert response.json[0]['name'] == "ToyCar"
