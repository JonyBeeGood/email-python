# email-python
import win32com.client
import os
from datetime import datetime, timedelta
outlook = win32com.client.Dispatch('outlook.application')
mapi = outlook.GetNamespace("MAPI")
for account in mapi.Accounts:
    print(account.DeliveryStore.DisplayName)
inbox = mapi.GetDefaultFolder(6)
messages = inbox.Items
received_dt = datetime.now() - timedelta(days=365)
received_dt = received_dt.strftime('%m/%d/%Y %H:%M %p')
messages = messages.Restrict("[SenderEmailAddress] = 'camila.dealmeida@rededor.com.br'")
outputDir = r"Documentos"
