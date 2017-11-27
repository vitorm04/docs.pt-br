---
title: "Colocação e obtenção condicional"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4ab4d0a97cbbaa2e5aaee25e0154e1cc94a82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-get-and-put"></a>Colocação e obtenção condicional
Este exemplo demonstra como usar o novo recuperar condicional e APIs de atualização para o modelo de programação WCF REST. Como recuperar condicional e atualização são mais apropriadas para orientada a recursos e serviços REST, este exemplo estende o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. Este exemplo se concentra na adição de suporte para recuperar condicional e atualize para o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) de exemplo usando as novas APIs introduzidas no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstra  
 Atualização e recuperar condicional  
  
## <a name="discussion"></a>Discussão  
 Neste exemplo, o serviço de WCF expõe uma coleção de clientes em um recurso orientado e a maneira REST. Para obter uma descrição detalhada da implementação do serviço, consulte o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo.  
  
 Este exemplo adiciona recuperar condicional e os recursos de atualização para o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. Condicional recuperar e atualizar use marcas de entidade HTTP e os cabeçalhos HTTP If-None-Match e If-Match para validar que os clientes têm ou não tem a entidade mais atual para um determinado recurso. No entanto, a implementação de código para analisar corretamente os cabeçalhos HTTP If-None-Match e If-Match pode ser tedioso e propenso a erros. Portanto, o <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> e <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> métodos foram adicionados para o <xref:System.ServiceModel.Web.IncomingWebRequestContext>, que pode ser acessado usando a instância atual do <xref:System.ServiceModel.Web.WebOperationContext>. Além disso, o `SetETag` método foi adicionado para o <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, tornando mais fácil retornar as marcas de entidade válido.  
  
 O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método se destina a ser usada com operações [WebGet]. Leva a tag de entidade atual para o recurso especificado como o `entityTag` parâmetro, que pode ser um `string`, `int`, `long` ou `Guid`. O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método verifica a tag de entidade com o cabeçalho HTTP If-None-Match da solicitação. Se a marca de entidade estiver presente no cabeçalho HTTP If-None-Match, em seguida, um <xref:System.ServiceModel.Web.WebFaultException> com um status de código de não modificado (304) é lançado; caso contrário, o método retorna. O mecanismo de recuperar condicional permite que o cliente para informar ao servidor que tem essa entidade e para enviar apenas a entidade atual, se o cliente não tiver. Exemplo de uso do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método pode ser visto no `GetCustomer` e `GetCustomers` operações do serviço. É importante observar que chama a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> não pode retornar. Os desenvolvedores devem implementar a operação para que a solicitação já é conhecida por ser bem-sucedida antes da chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> é executada, como se a chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> foi não está presente, o serviço envia uma resposta com um código de status bem-sucedido.  
  
 O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método é semelhante de <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método. Também usa a marca de entidade atual para o recurso especificado. No entanto, destina-se a ser usada com operações [WebInvoke] no qual o método é definido como "PUT" ou "Excluir". O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método verifica a tag de entidade com o cabeçalho HTTP If-Match da solicitação. Se a marca de entidade não está presente no cabeçalho HTTP If-Match, em seguida, um <xref:System.ServiceModel.Web.WebFaultException> com um status de código de falha de pré-condição (412) é gerado. O mecanismo de atualização condicional permite que o cliente para informar ao servidor que tem essa entidade para o recurso e para permitir que somente o cliente alterar o recurso. Se a entidade tiver é atual. Exemplo de uso do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método pode ser visto no `UpdateCustomer` e `DeleteCustomer` operações do serviço. Assim como ocorre com <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, é importante observar que chama a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> não pode retornar. Os desenvolvedores devem implementar a operação, de modo que a solicitação já é conhecida por ser bem-sucedida antes da chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> é executada, como se a chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> não estava presente, o serviço deve responder com um código de status bem-sucedido.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que é executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo condicional Get e Put. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para executar o exemplo com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e escolhendo **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione CTRL + F5 para executar o projeto de aplicativo de console. Se este projeto com depuração habilitada (pressionando F5, em vez de CTRL + F5), o depurador será interrompido quando uma exceção é lançada pela condicional obter e colocar a verificação. Quando isso acontece, pressione F5 para continuar a executar o exemplo.  
  
3.  A janela do console aparecem areia fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução.  
  
4.  Como o exemplo é executado, o cliente envia solicitações ao serviço e grava as respostas para a janela do console.  
  
5.  Pressione qualquer tecla para encerrar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
