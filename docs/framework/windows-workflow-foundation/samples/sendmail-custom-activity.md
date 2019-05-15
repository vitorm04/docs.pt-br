---
title: Atividade personalizado de SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: d760f95b8e98bae52341296b90008e72d5c47d1f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637665"
---
# <a name="sendmail-custom-activity"></a>Atividade personalizado de SendMail
Este exemplo demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho. A atividade personalizada usa os recursos do <xref:System.Net.Mail.SmtpClient> para enviar email de forma assíncrona e enviar email com autenticação. Também fornece alguns recursos de usuário final como o modo de teste, a substituição de token, os modelos de arquivo, e o caminho da operação de teste.  
  
 A tabela a seguir detalha os argumentos para atividades de `SendMail` .  
  
|Nome|Tipo|Descrição|  
|-|-|-|  
|Host|Cadeia de Caracteres|Endereço do host de servidor SMTP.|  
|Porta|Cadeia de Caracteres|Porta de serviço SMTP no host.|  
|EnableSsl|bool|Especifica se <xref:System.Net.Mail.SmtpClient> usar secure sockets (SSL) para criptografar a conexão.|  
|UserName|Cadeia de Caracteres|Nome de usuário para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.|  
|Senha|Cadeia de Caracteres|Senha para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.|  
|Assunto|<xref:System.Activities.InArgument%601>\<string>|Assunto de mensagem.|  
|Corpo|<xref:System.Activities.InArgument%601>\<string>|Corpo da mensagem.|  
|Anexos|<xref:System.Activities.InArgument%601>\<string>|Coleção de anexos usada para armazenar dados anexados a esta mensagem de email.|  
|De|<xref:System.Net.Mail.MailAddress>|Endereço para essa mensagem de email.|  
|Para|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Coleção de endereços que contém os destinatários desta mensagem de email.|  
|CÓPIA CARBONO|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Trata da coleção que contém os destinatários CC (cópia carbono) desta mensagem de email.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Coleção de endereços que contém os destinatários com cópia oculta (Cco) desta mensagem de email.|  
|Tokens|<xref:System.Activities.InArgument%601>< IDictionary\<cadeia de caracteres, cadeia de caracteres >>|Tokens a substituição no corpo. Esse recurso permite que os usuários especifiquem alguns valores no corpo do que pode ser substituído pelos tokens fornecidos posteriormente usando essa propriedade.|  
|BodyTemplateFilePath|Cadeia de Caracteres|Caminho de um modelo para o corpo. A atividade de `SendMail` copia o conteúdo do arquivo a sua propriedade body.<br /><br /> O modelo pode conter os tokens que são substituídos pelos conteúdos da propriedade tokens.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Quando essa propriedade é definida, todos os emails são enviados para o endereço especificado nele.<br /><br /> Esta propriedade destina-se a ser usada ao testar fluxos de trabalho. Por exemplo, quando você deseja ter certeza de que todos os emails são enviados sem enviar aos destinatários reais.|  
|TestDropPath|Cadeia de Caracteres|Quando essa propriedade é definida, todos os emails também são salvas no arquivo especificado.<br /><br /> Esta propriedade destina-se a ser usado quando você está testando ou depurando fluxos de trabalho, para certificar-se de que o formato e o conteúdo dos emails de saída é apropriada.|  
  
## <a name="solution-contents"></a>Conteúdo de solução  
 A solução contém dois projetos.  
  
|Projeto|Descrição|Arquivos importantes|  
|-------------|-----------------|---------------------|  
|SendMail|A atividade de SendMail|1.  SendMail.cs: implementação para atividades principal<br />2.  SendMailDesigner.xaml e SendMailDesigner.xaml.cs: designer para atividades de SendMail<br />3.  MailTemplateBody.htm: modelo para o email é mandado.|  
|SendMailTestClient|Cliente para testar a atividade de SendMail.  Este projeto mostra duas maneiras para chamar a atividade de SendMail: declarativamente, e programaticamente.|1.  Sequence1.xaml: fluxo de trabalho que chama a atividade de SendMail.<br />2.  Module.vb: chama Sequence1 e também cria um fluxo de trabalho de programação que usa SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Configuração adicional de atividade de SendMail  
 Embora não mostrado no exemplo, os usuários podem executar a configuração de adição de atividade de SendMail. As três seções a seguir demonstram como este é feita.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Enviando um email usando os tokens especificados no corpo  
 Este snippet de código demonstra como você pode enviar email com tokens no corpo. Observe como os tokens são fornecidos na propriedade body. Os valores para estes tokens são fornecidos para a propriedade tokens.  
  
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
 Este snippet mostra como enviar um email usando tokens de um modelo no corpo. Observe que ao definir a propriedade de `BodyTemplateFilePath` não precisamos de fornecer o valor para a propriedade body (o conteúdo do arquivo de modelo serão copiados para o corpo).  
  
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
 Este trecho de código mostra como definir as duas propriedades testando: definindo `TestMailTo` a todas as mensagens serão enviadas para `john.doe@contoso.con` (sem consideração os valores de para, Cc, Cco). Definindo TestDropPath todos os email de saída também serão gravados no caminho fornecido. Essas propriedades podem ser definidas independentes (não são relacionadas).  
  
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
  
 Para obter mais informações sobre como configurar um servidor SMTP, consulte os links a seguir.  
  
- [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [Configurando o serviço SMTP (IIS 6.0)](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [IIS 7.0: Configurar o email SMTP](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [Como instalar o serviço SMTP](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Os emuladores SMTP fornecidos por terceiros estão disponíveis para download.  
  
##### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1. Usando o Visual Studio 2010, abra o arquivo de solução de Sendmail.  
  
2. Certifique-se de que você tem acesso a um servidor SMTP válido. Consulte as instruções de configuração.  
  
3. Configure o programa com o endereço do servidor e de e para endereços de email.  
  
     Para executar corretamente este exemplo, talvez você precise configurar o valor de e para endereços de email e o endereço do servidor SMTP em Module. vb e em Sequence. Você precisará alterar o endereço nos dois lugares como o envia email de programa em duas maneiras diferentes  
  
4. Para criar a solução, pressione CTRL+SHIFT+B.  
  
5. Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
