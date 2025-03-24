# - Часть 1: Тестирование REST API
https://d33333-6380.postman.co/workspace/d-Workspace~f142a0fe-bb72-42d4-81de-a81614baa59c/run/36514939-cbcc2b7d-e2ff-4665-ac6e-c6bb8b5b0166

Автотест 

import requests

BASE_URL = "https://jsonplaceholder.typicode.com/posts"

def test_create_post():
    new_post = {
        "title": "котик",
        "body": "черный котик",
        "userId": 22
    }
    response = requests.post(BASE_URL, json=new_post)
    assert response.status_code == 201
    response_data = response.json()
    assert response_data["title"] == new_post["title"]

def test_update_post():
    updated_post = {
        "title": "котэ",
        "body": "белый котэ",
        "userId": 22
    }
    response = requests.put(f"{BASE_URL}/22", json=updated_post)
    assert response.status_code == 200
    response_data = response.json()
    assert response_data["title"] == "котэ"

def test_delete_post():
    response = requests.delete(f"{BASE_URL}/22")
    assert response.status_code == 200
    assert response.text == ''

