# import vk_api
import random
import time
token = ""


vk = vk_api.VkApi(token=token)

vk._auth_token()

while True:
    try:
        messages = vk.method("messages.getConversations", {"offset": 0, "count": 20, "filter": "unanswered"})
        if messages["count"] >= 1:
            id = messages["items"][0]["last_message"]["from_id"]
            body = messages["items"][0]["last_message"]["text"]
            if body.lower() == "привет":
                vk.method("messages.send", {"peer_id": id, "message": "Привет!", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "hi":
                vk.method("messages.send", {"peer_id": id, "message": "Привет!", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто я?":
                vk.method("messages.send", {"peer_id": id, "message": "ты хороший человек", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто я ?":
                vk.method("messages.send", {"peer_id": id, "message": "ты хороший человек", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто я":
                vk.method("messages.send", {"peer_id": id, "message": "ты хороший человек", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто твой создатель":
                vk.method("messages.send", {"peer_id": id, "message": "*illedan1 (хреновый программист)", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто твой создатель?":
                vk.method("messages.send", {"peer_id": id, "message": "*illedan1 (хреновый программист)", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто твой создатель ?":
                vk.method("messages.send", {"peer_id": id, "message": "*illedan1 (хреновый программист)", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "hellp":
                vk.method("messages.send", {"peer_id": id, "message": "привет,кто я?,кто твой создатель,hellp", "random_id": random.randint(1, 2147483647)})
            else:
                vk.method("messages.send", {"peer_id": id, "message": "я не знаю что значит: " + str(body.lower()), "random_id": random.randint(1, 2147483647)})
    except Exception as E:
        time.sleep(1)