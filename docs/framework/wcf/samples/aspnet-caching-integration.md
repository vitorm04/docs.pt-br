---
title: Integração de cache ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 8ed546459479e9986d6bbecf6eaca350d2d73c98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770016"
---
# <a name="aspnet-caching-integration"></a>Integração de cache ASP.NET
Este exemplo demonstra como utilizar o cache de saída ASP.NET com o modelo de programação WCF WEB HTTP. Este tópico enfoca o recurso de integração de cache de saída do ASP.NET.  
  
## <a name="demonstrates"></a>Demonstra  
 Integração com o Cache de saída do ASP.NET  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Discussão  
 O exemplo usa o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET de utilizar o cache de saída com o serviço do Windows Communication Foundation (WCF). O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é aplicada às operações de serviço e fornece o nome de um perfil de cache em um arquivo de configuração que deve ser aplicado às respostas de determinada operação.  
  
 No arquivo Service.cs do projeto de serviço de exemplo, tanto a `GetCustomer` e `GetCustomers` operações são marcadas com o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, que fornece o nome do perfil de cache "CacheFor60Seconds". No arquivo Web. config do projeto de serviço, o perfil de cache "CacheFor60Seconds" é fornecido sob o <`caching`> elemento <`system.web`>. Para este perfil de cache, o valor da `duration` atributo é "60", portanto, as respostas associadas a esse perfil são armazenados em cache no cache de saída ASP.NET para 60 segundos. Além disso, para este perfil de cache, o `varmByParam` atributo é definido como "formato" Portanto, solicitações com valores diferentes para o `format` consulta ao parâmetro de cadeia de caracteres têm suas respostas em cache separadamente. Por fim, o perfil de cache `varyByHeader` atributo é definido como "Aceitar", para que as solicitações com diferentes valores do cabeçalho Accept tenham suas respostas em cache separadamente.  
  
 Program.cs no projeto do cliente demonstra como esse cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço usando outras classes do .NET Framework, como a fábrica de canais do WCF e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço HTTP básico](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo) ilustram como usar essas classes para se comunicar com um serviço WCF.  
  
## <a name="to-run-the-sample"></a>Para executar a amostra  
 O exemplo consiste em três projetos:  
  
-   **Serviço**: Um projeto de aplicativo Web que inclui um serviço de HTTP do WCF hospedado no ASP.NET.  
  
-   **Cliente**: Um projeto de aplicativo de console que faz chamadas para o serviço.  
  
-   **Common**: Uma biblioteca compartilhada que contém o tipo de cliente usado pelo cliente e serviço.  
  
 Como o aplicativo de console do cliente é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução para o exemplo de integração de cache do ASP.NET.  
  
2. Pressione CTRL+SHIFT+B para criar a solução.  
  
3. Se o **Gerenciador de soluções** janela não ainda estiver aberta, pressione CTRL + W + S.  
  
4. Dos **Gerenciador de soluções** janela, o botão direito do mouse a **Service** do projeto e selecione **iniciar uma nova instância**. Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5. Dos **Gerenciador de soluções** janela, o botão direito do mouse a **cliente** do projeto e selecione **iniciar uma nova instância**.  
  
6. A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda. A qualquer momento, você pode exibir a página de ajuda HTML, digitando o URI da página de Ajuda em um navegador.  
  
7. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
8. Pressione qualquer tecla para encerrar o aplicativo de console do cliente.  
  
9. Pressione SHIFT + F5 para parar a depuração de serviço.  
  
10. Na área de notificação do Windows, clique com botão direito no ícone do ASP.NET development server e selecione **parar**.
