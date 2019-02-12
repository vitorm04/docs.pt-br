---
title: Operações assíncronas (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 1aa51d07be6073a75ef40ade83eba13371db3a69
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56094146"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Operações assíncronas (WCF Data Services)
Os aplicativos Web devem acomodar uma latência maior entre cliente e servidor do que os aplicativos que são executados dentro das redes internas. Para otimizar o desempenho e a experiência do usuário do seu aplicativo, recomendamos usar os métodos assíncronos das classes <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601> ao acessar servidores do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pela Web.  
  
 Embora os servidores do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] processem as solicitações HTTP de forma assíncrona, alguns métodos de bibliotecas de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] são síncronos e aguardam até que a troca inteira de solicitação-resposta esteja concluída antes de continuar a execução. Os métodos assíncronos das bibliotecas de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] não aguardam essa troca para concluir e podem permitir que o aplicativo mantenha uma interface de usuário enquanto isso.  
  
 Você pode executar operações assíncronas usando um par de métodos na <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601> classes que começam com *Begin* e *final* , respectivamente. O *começar* métodos de registram um delegado que o serviço chama quando a operação for concluída. O *final* métodos devem ser chamados no delegado que está registrado para manipular o retorno de chamada das operações concluídas. Quando você chama o *final* método para concluir uma operação assíncrona, você deve fazer isso da mesma <xref:System.Data.Services.Client.DataServiceQuery%601> ou <xref:System.Data.Services.Client.DataServiceContext> instância que você usou para iniciar a operação. Cada *começar* leva um `state` parâmetro que pode passar um objeto de estado para o retorno de chamada. Esse objeto de estado é recuperado do <xref:System.IAsyncResult> que é fornecida com o retorno de chamada e é usado para chamar correspondente *final* método para concluir a operação assíncrona. Por exemplo, quando você fornece a instância <xref:System.Data.Services.Client.DataServiceQuery%601> como o parâmetro `state` quando chama o método <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> na instância, a mesma instância <xref:System.Data.Services.Client.DataServiceQuery%601> é retornada pelo <xref:System.IAsyncResult>. Essa instância de <xref:System.Data.Services.Client.DataServiceQuery%601> é em seguida usada para chamar o método <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> para concluir a operação de consulta. Para obter mais informações, confira [Como: Executar consultas de serviço de dados assíncronos](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Somente operações assíncronas têm suporte pelas bibliotecas de cliente que são fornecidas no .NET Framework para Silverlight. Para obter mais informações, consulte [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 As bibliotecas de cliente do .NET Framework dão suporte às seguintes operações assíncronas:  
  
|Operação|Métodos|  
|---------------|-------------|  
|Executando uma <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Executando uma consulta do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Executando uma consulta em lote do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Carregando uma entidade relacionada no <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Salvando alterações nos objetos no <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Considerações de threads para operações assíncronas  
 Em um aplicativo multi-threaded, o delegado que é registrado como um retorno de chamada para a operação assíncrona não é necessariamente chamado no mesmo thread que foi usado para chamar o *começar* método, que cria a solicitação inicial. Em um aplicativo em que o retorno de chamada deve ser chamado em um thread específico, você deverá explicitamente empacotar a execução do *final* método, que manipula a resposta, o thread desejado. Por exemplo, em aplicativos baseados no Windows Presentation Foundation (WPF) e aplicativos baseados no Silverlight, a resposta deverá ser lido de volta para o thread de interface de usuário usando o método <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> no objeto <xref:System.Windows.Threading.Dispatcher>. Para obter mais informações, consulte [consultando o Data Service (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Consulte também
- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
