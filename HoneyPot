import pyinotify
from telethon import TelegramClient
from telethon import sync, events
import requests
 
api_id =  # int
api_hash = ""
 
client  = TelegramClient("Name", api_id, api_hash)
 
client.start()
 
dlgs = client.get_dialogs()
 
class MyEventHandler(pyinotify.ProcessEvent):
    def process_IN_ACCESS(self, event):
        client.send_message("Доступ к наблюдаемому элементу или файлу в отслеживаемом каталоге, например, чтение файла")
 
    def process_IN_ATTRIB(self, event):
        client.send_message("Метаданные отслеживаемого элемента или файла в отслеживаемом каталоге изменяются")
 
    def process_IN_CLOSE_NOWRITE(self, event):
        client.send_message("Файл или каталог, открытый для записи, закрыт")
 
    def process_IN_CLOSE_WRITE(self, event):
        client.send_message("Файл или каталог, открытый только для чтения, закрывается")
 
    def process_IN_CREATE(self, event):
        client.send_message("Создание подкаталогов или файлов в отслеживаемом каталоге")
 
    def process_IN_DELETE(self, event):
        client.send_message("Удалить каталоги или файлы в контролируемом каталоге")
 
    def process_IN_MODIFY(self, event):
        client.send_message("Контролируемый элемент или файлы в отслеживаемом каталоге изменяются")
 
    def process_IN_OPEN(self, event):
        client.send_message("Файл или каталог открыт")
    
    def process_IN_MOVED_FROM(self, event):
        client.send_message("Файлы или каталоги перемещаются в область мониторинга")

    def process_IN_MOVED_TO(self, event):
        client.send_message("Файлы или каталоги перемещаются в область мониторинга")
 

def main():
    wm = pyinotify.WatchManager()
    wm.add_watch("dir", pyinotify.ALL_EVENTS, rec=True)
    eh = MyEventHandler()
    notifier = pyinotify.Notifier(wm, eh)
    notifier.loop()
 
if __name__ == "__main__":
    main()
