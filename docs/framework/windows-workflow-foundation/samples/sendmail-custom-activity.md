---
title: Atividade personalizado de SendMail
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb8454d3e1e679154bc016e37b83c3ac4ff6768
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="sendmail-custom-activity"></a>Atividade personalizado de SendMail
Este exemplo demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho. A atividade personalizado usa os recursos de <xref:System.Net.Mail.SmtpClient> de forma assíncrona enviar email e enviar email com autenticação. Também fornece alguns recursos de usuário final como o modo de teste, a substituição de token, os modelos de arquivo, e o caminho da operação de teste.  
  
 A tabela a seguir detalha os argumentos para atividades de `SendMail` .  
  
|Nome|Tipo|Descrição|  
|-|-|-|  
|Host|Cadeia de caracteres|Endereço do host de servidor SMTP.|  
|Porta|Cadeia de caracteres|Porta de serviço SMTP no host.|  
|EnableSsl|bool|Especifica se <xref:System.Net.Mail.SmtpClient> usar secure sockets (SSL) para criptografar a conexão.|  
|UserName|Cadeia de caracteres|Nome de usuário para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.|  
|Senha|Cadeia de caracteres|Senha para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.|  
|Assunto|<xref:System.Activities.InArgument%601>\<cadeia de caracteres >|Assunto de mensagem.|  
|Corpo|<xref:System.Activities.InArgument%601>\<cadeia de caracteres >|Corpo da mensagem.|  
|Anexos|<xref:System.Activities.InArgument%601>\<cadeia de caracteres >|Coleção de anexo usada para armazenar dados anexados a esta mensagem de email.|  
|De|<xref:System.Net.Mail.MailAddress>|O endereço para esta mensagem de email.|  
|Para|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Trata da coleção que contém os destinatários esta mensagem de email.|  
|CÓPIA CARBONO|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Trata da coleção que contém os destinatários de (CC) de impressão carbono para esta mensagem de email.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Trata da coleção que contém os destinatários de (BCC) de impressão carbono cego para esta mensagem de email.|  
|Tokens|<xref:System.Activities.InArgument%601>< IDictionary\<cadeia de caracteres, cadeia de caracteres >>|Tokens a substituição no corpo. Esse recurso permite que os usuários especifiquem alguns valores no corpo do que pode ser substituído pelos tokens fornecidos posteriormente usando essa propriedade.|  
|BodyTemplateFilePath|Cadeia de caracteres|Caminho de um modelo para o corpo. A atividade de `SendMail` copia o conteúdo do arquivo a sua propriedade body.<br /><br /> O modelo pode conter os tokens que são substituídos pelos conteúdos da propriedade tokens.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Quando essa propriedade é definida, todos os email são enviados para o endereço especificado nele.<br /><br /> Esta propriedade destina-se a ser usada ao testar fluxos de trabalho. Por exemplo, quando você desejar se certificar de que todos os email são enviados sem enviar aos destinatários reais.|  
|TestDropPath|Cadeia de caracteres|Quando essa propriedade é definida, todos os email são salvos também no arquivo especificado.<br /><br /> Esta propriedade destina-se a ser usada quando você está testando ou depurando fluxos de trabalho, para certificar-se de que o formato e conteúdo de email de saída são apropriadas.|  
  
## <a name="solution-contents"></a>Conteúdo de solução  
 A solução contém dois projetos.  
  
|Projeto|Descrição|Arquivos importantes|  
|-------------|-----------------|---------------------|  
|SendMail|A atividade de SendMail|1.  SendMail.cs: implementação para atividades principal<br />2.  SendMailDesigner.xaml e SendMailDesigner.xaml.cs: designer para atividades de SendMail<br />3.  MailTemplateBody.htm: modelo para o email é mandado.|  
|SendMailTestClient|Cliente para testar a atividade de SendMail.  Este projeto mostra duas maneiras para chamar a atividade de SendMail: declarativamente, e programaticamente.|1.  Sequence1.xaml: fluxo de trabalho que chama a atividade de SendMail.<br />2.  Module.vb: chama Sequence1 e também cria um fluxo de trabalho de programação que usa SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Configuração adicional de atividade de SendMail  
 Embora não mostrado no exemplo, os usuários podem executar a configuração de adição de atividade de SendMail. As três seções a seguir demonstram como este é feita.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Enviando um email usando os tokens especificados no corpo  
 Este trecho de código demonstra como você pode enviar email com tokens no corpo. Observe como os tokens são fornecidos na propriedade body. Os valores para estes tokens são fornecidos para a propriedade tokens.  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>Enviando um email usando um modelo  
 Este trecho mostra como enviar um email usando tokens de um modelo no corpo. Observe que ao definir a propriedade de `BodyTemplateFilePath` não precisamos de fornecer o valor para a propriedade body (o conteúdo do arquivo de modelo serão copiados para o corpo).  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>Enviar email no modo de teste  
 Este trecho de código mostra como definir as duas propriedades de teste: definindo `TestMailTo` para todas as mensagens serão enviadas para john.doe@contoso.con (sem levar em consideração dos valores de para, Cc, Cco). Definindo TestDropPath todos os email de saída também serão gravados no caminho fornecido. Essas propriedades podem ser definidas independentes (não são relacionadas).  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>Instruções de configuração  
 O acesso a um servidor SMTP é necessário para esse exemplo.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando um servidor SMTP, consulte os links a seguir.  
  
-   [Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Configurando o serviço SMTP (IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: Configurar o email SMTP](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Como instalar o serviço SMTP](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Os emuladores SMTP fornecidos por terceiros estão disponíveis para download.  
  
##### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de SendMail.sln.  
  
2.  Certifique-se de que você tem acesso a um servidor SMTP válido. Consulte as instruções de configuração.  
  
3.  Configurar o programa com seu endereço do servidor, e e endereços de email.  
  
     Para executar corretamente esse exemplo, você pode precisar configurar o valor e endereços de email e o endereço de servidor SMTP em Module.vb e em Sequence.xaml. Você precisará alterar o endereço nos dois lugares como o envia email de programa em duas maneiras diferentes  
  
4.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
5.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`