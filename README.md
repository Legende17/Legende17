import smtplib
import random
import time

# Liste mit möglichen E-Mail-Adressen für den Versand
email_addresses = ['sender1@example.com', 'sender2@example.com', 'sender3@example.com']

# Funktion zum Versenden einer E-Mail
def send_email(sender, receiver, subject, body):
    try:
        smtp_obj = smtplib.SMTP('smtp.gmail.com', 587)
        smtp_obj.starttls()
        smtp_obj.login(sender, 'Deinemudda123')  

        message = f"Subject: {subject}\n\n{body}"
        smtp_obj.sendmail(sender, receiver, message)
        smtp_obj.quit()
        return True
    except Exception as e:
        print("Fehler beim Versenden der E-Mail:", e)
        return False

# Hauptfunktion für den Bot
def email_bot():
    receiver = 'doenervorstand.bw@gmail.com'  # Empfängeradresse hier eintragen
    subject = 'Simulation: Spam-E-Mails'
    body = 'Dies ist eine Spam-E-Mail für das Schulprojekt. JaJaJa'

    for _ in range(100):  # 100 Spam-E-Mails senden
        sender = random.choice(email_addresses)  # Zufälligen Absender wählen
        send_email(sender, receiver, subject, body)
        time.sleep(1)  # Eine Sekunde Pause zwischen den E-Mails

    print("Spam-E-Mails wurden erfolgreich gesendet.")

if __name__ == "__main__":
    email_bot()
