# info de entrega / erro
```
select 
    whatsapp, 
    company_id,
    enterprise_id,
    development_id,
    customer_id,
    whatsapp_state_delivered_at,
    whatsapp_falure_reason,
    whatsapp_twilio_error_code,
    whatsapp_twilio_error_description,
    whatsapp_twilio_error_message,
    whatsapp_kustomer_error_code,
    whatsapp_kustomer_error_description,
    whatsapp_kustomer_error_message,    
from prod.raw_notifications.raw_customer_notification
limit 10
```

# info de whatsapp reachable
```
select 
    parse_json(first_message_in):channel::string channel,
    parse_json(first_message_in):createdAt::string last_message_in,
    parse_json(first_message_in):meta:from::string,
    parse_json(first_message_in):meta:to::string,
from prod.raw_kustomer.raw_kustomer_conversations
where first_message_in::string <> '{}' and channel = 'whatsapp'
limit 10
```

# info de whatsapp validado
```
select 
    created_at last_app_login, 
    notification_phone_country_code,
    notification_phone_number,
    company_id,
    enterprise_id,
    development_id,
    customer_id    
from prod.raw_apps_interactions_tracking.raw_apps_interactions_tracking_events
limit 10
```

# LISTA DE WHATSAPP SAFE TO MESSAGE NO BANCO DO WEBHOOKS DO NOTIFICATIONS


# LISTA DE BSUIDS NO WEBHOOKS DO KUSTOMER (MESSAGES) -> TO_PHONE, BSUID_ACCOUNT, ETC



# PRIORIDADES

1. IMPLEMENTAR CAMPOS DE BSUID DENTRO DO C3
2. 
3. FLUXO DE COLETA DE PHONE NA LIA (COM TEMPLATE PARA SOLICITAÇÃO DE INFO DE CONTATO)
4. FLUXO DE COLETA DE PHONE NO TWILIO (COM TEMPLATE PARA SOLICITAÇÃO DE INFO DE CONTATO)
5. MAGIC LINK PARA GERAÇÃO DE TOKEN
6. FLUXO DE COLETA DE CUSTOMER_ID NA LIA USANDO O MAGIC LINK
7. FLUXO DE COLETA DE CUSTOMER_ID NO TWILIO USANDO O MAGIC LINK
8. APP NO KUSTOMER + ADMIN PARA MERGE DE CLIENTES COM APENAS BSUID COM ALGUM CLIENTE ATUAL: PERMITIR ESCOLHA 
9.  
10. X
11. X
12. X
13. X
14. X
15. X
16. X

-- CRIAR TABELA DE BSUIDS
{ BSUID | PHONE | BUSINESS_PORT | DOCUMENT(SE AUTH) }
