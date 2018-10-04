---
title: Serviço básico de HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 2e4aee93341404df5f06b096a9a7bf18a3c94f56
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48262376"
---
# <a name="basic-http-service"></a>Serviço básico de HTTP
Este exemplo demonstra como implementar um serviço baseado em HTTP e baseados em RPC - popularmente conhecido como serviço "POX" (Plain Old XML) – usando o modelo de programação de REST do Windows Communication Foundation (WCF). Esse exemplo consiste em dois componentes: um serviço auto-hospedado do HTTP do WCF (Service.cs) e um aplicativo de console (Program.cs) que cria o serviço e faz chamadas para ele.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O serviço do WCF expõe 2 operações, `EchoWithGet` e `EchoWithPost`, que retorna a cadeia de caracteres que foi passada como entrada.  
  
 O `EchoWithGet` operação é anotada com <xref:System.ServiceModel.Web.WebGetAttribute>, que indica que a operação processa HTTP `GET` solicitações. Porque o <xref:System.ServiceModel.Web.WebGetAttribute> não especificar explicitamente uma <xref:System.UriTemplate>, a operação de espera que a cadeia de caracteres de entrada a ser passado usando um parâmetro de cadeia de caracteres de consulta com o nome `s`. Observe que o formato do URI que espera que o serviço pode ser personalizado usando o <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> propriedade.  
  
 O `EchoWithPost` operação é anotada com <xref:System.ServiceModel.Web.WebInvokeAttribute>, que indica que ele não é um `GET` operação (tem efeitos colaterais). Porque o <xref:System.ServiceModel.Web.WebInvokeAttribute> não especificar explicitamente uma `Method`, a operação processa HTTP `POST` as solicitações que têm a cadeia de caracteres no corpo da solicitação (em formato XML, por exemplo). Observe que o método HTTP e o formato do URI da solicitação podem ser personalizados usando o <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> e <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> propriedades, respectivamente.  
  
 O arquivo App. config configura o serviço WCF com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> propriedade definida como `true`. Como resultado, a infraestrutura do WCF cria uma página de ajuda baseados em HTML automática em `http://localhost:8000/Customers/help` que fornece informações sobre como construir solicitações HTTP para o serviço e como consumir a resposta do serviço HTTP.  
  
 Program.cs demonstra como uma fábrica de canais do WCF pode ser usada para fazer chamadas para as respostas de serviço e de processo. Observe que isso é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço de uso de outras classes do .NET Framework, como <xref:System.Net.HttpWebRequest> e <xref:System.Net.WebClient>.
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que ambos executados em um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução para o exemplo de serviço Http básico. Ao iniciar o Visual Studio 2012, você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando duas vezes no ícone do Visual Studio 2012 e selecionando **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o aplicativo de console sem depuração. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda. A qualquer momento, você pode exibir a página de ajuda HTML, digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
3.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
