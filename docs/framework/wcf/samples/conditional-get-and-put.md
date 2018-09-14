---
title: Colocação e obtenção condicional
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: 29819f89327128cdd71cc89eb8d14126522dc2df
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595117"
---
# <a name="conditional-get-and-put"></a>Colocação e obtenção condicional
Este exemplo demonstra como usar o novo recuperar condicional e APIs de atualização para o modelo de programação REST do WCF. Como recuperar condicional e atualização são mais apropriados para orientada a recursos e serviços REST, este exemplo amplia a [serviço básico de recursos](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. Este exemplo se concentra em Adicionar suporte para recuperar condicional e a atualização do [serviço básico de recursos](../../../../docs/framework/wcf/samples/basic-resource-service.md) de exemplo usando as novas APIs introduzidas no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstra  
 Atualização e como recuperar condicional  
  
## <a name="discussion"></a>Discussão  
 O serviço WCF neste exemplo expõe uma coleção de clientes em um recurso orientado e uma maneira REST. Para obter uma descrição detalhada da implementação do serviço, consulte o [serviço de recurso básico](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo.  
  
 Este exemplo adiciona condicional recupere e recursos de atualização para o [serviço de recurso básico](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. Condicional recuperar e atualizar marcas de entidade HTTP de uso e os cabeçalhos HTTP If-None-Match e If-Match para validar que os clientes têm ou não tem a entidade mais atual para um determinado recurso. No entanto, a implementar o código para analisar corretamente os cabeçalhos HTTP If-None-Match e If-Match pode ser entediante e propenso a erro. Portanto, o <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> e <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> métodos foram adicionados para o <xref:System.ServiceModel.Web.IncomingWebRequestContext>, que pode ser acessada usando a instância atual do <xref:System.ServiceModel.Web.WebOperationContext>. Além disso, o `SetETag` foi adicionado ao método o <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, tornando mais fácil ao retornar marcas de entidade válido.  
  
 O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método é destinado a ser usado com operações [WebGet]. Ele usa a marca da entidade atual para o recurso determinado como o `entityTag` parâmetro, que pode ser um `string`, `int`, `long` ou `Guid`. O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método verifica a marca da entidade contra o cabeçalho HTTP If-None-Match da solicitação. Se a marca da entidade estiver presente no cabeçalho HTTP If-None-Match, em seguida, um <xref:System.ServiceModel.Web.WebFaultException> com um status de código de não modificado (304) é lançado; caso contrário, o método retorna. O mecanismo de recuperar condicional permite que o cliente para informar o servidor que tem essa entidade e para enviar apenas a entidade atual, se o cliente não o tiver. Exemplo de uso do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método pode ser visto na `GetCustomer` e `GetCustomers` operações do serviço. É importante observar que chama a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> não pode retornar. Os desenvolvedores devem implementar a operação para que a solicitação já é conhecida por ser bem-sucedida antes de chamar <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> é executado, como que, se a chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> foi não estiver presente, o serviço enviará uma resposta com um código de status bem-sucedido.  
  
 O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método é semelhante ao <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método. Ele também usa a marca da entidade atual para o recurso determinado. No entanto, destina-se a ser usado com operações [WebInvoke] no qual o método é definido como "PUT" ou "Excluir". O <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método verifica a marca da entidade contra o cabeçalho If-Match de HTTP da solicitação. Se a marca da entidade não estiver presente no cabeçalho HTTP If-Match, em seguida, um <xref:System.ServiceModel.Web.WebFaultException> com um status de código de falha de pré-condição (412) é gerado. O mecanismo de atualização condicional permite que o cliente para informar o servidor que tem essa entidade para o recurso e para permitir que somente o cliente alterar o recurso. Se a entidade tiver é atual. Exemplo de uso do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> método pode ser visto na `UpdateCustomer` e `DeleteCustomer` operações do serviço. Assim como ocorre com <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, é importante observar que chama a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> não pode retornar. Os desenvolvedores devem implementar a operação, de modo que a solicitação já é conhecida por ser bem-sucedida antes de chamar <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> é executado, tal que, se a chamada para <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> não estava presente, o serviço responderia com um código de status bem-sucedido.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que é executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo condicional Get e Put. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para executar o exemplo com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e escolhendo **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione CTRL + F5 para executar o projeto de aplicativo de console. Se este projeto com a depuração habilitada (pressionando F5, em vez de CTRL + F5), o depurador para quando uma exceção é gerada pelo condicional obter e colocar a verificação. Quando isso acontece, pressione F5 para continuar a executar o exemplo.  
  
3.  A janela console aparecer areia fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução.  
  
4.  Como o exemplo é executado, o cliente envia solicitações ao serviço e grava as respostas para a janela do console.  
  
5.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
