---
title: 'Como: usar o moniker de serviço do Windows Communication Foundation sem registro'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918574"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="57445-102">Como: usar o moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="57445-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="57445-103">Para conectar e se comunicar com um serviço do Windows Communication Foundation (WCF), um aplicativo de cliente do WCF deve ter os detalhes do contrato de serviço, a configuração de associação e o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="57445-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="57445-104">Geralmente, o moniker de serviço do WCF obtém o contrato exigido por meio do registro anterior dos tipos de atributo necessário, mas pode haver casos em que isso não é viável.</span><span class="sxs-lookup"><span data-stu-id="57445-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="57445-105">No lugar do registro, o moniker pode obter a definição do contrato na forma de um documento WSDL Web Services Definition Language (), com o uso do `wsdl` parâmetro ou por meio da troca de metadados, através do uso do `mexAddress` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="57445-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="57445-106">Isso permite cenários como a distribuição de uma planilha do Excel em que alguns dos valores de célula são calculados por meio de interações de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="57445-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="57445-107">Nesse cenário, talvez não seja viável para registrar o assembly do contrato de serviço em todos os clientes que podem abrir o documento.</span><span class="sxs-lookup"><span data-stu-id="57445-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="57445-108">O `wsdl` parâmetro ou o `mexAddress` parâmetro permite que uma solução independente.</span><span class="sxs-lookup"><span data-stu-id="57445-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57445-109">A autenticação mútua deve ser usada para proteger contra a solicitação e resposta de falsificação ou adulteração.</span><span class="sxs-lookup"><span data-stu-id="57445-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="57445-110">Especificamente, é importante para os clientes para ter certeza de que o ponto de extremidade de troca de metadados que está respondendo é a parte confiável desejado.</span><span class="sxs-lookup"><span data-stu-id="57445-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57445-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57445-111">Example</span></span>  
 <span data-ttu-id="57445-112">Este exemplo mostra o uso do moniker de serviço com um contrato MEX.</span><span class="sxs-lookup"><span data-stu-id="57445-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="57445-113">Um serviço com o seguinte contrato é exposto com wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="57445-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="57445-114">Pode ser usado construir um cliente WCF para o serviço remoto a cadeia de caracteres de moniker de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="57445-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="57445-115">Durante a execução do aplicativo cliente, o cliente executa um `WS-MetadataExchange` fornecido `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="57445-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="57445-116">Isso pode retornar o endereço, associação e detalhes do contrato para um número de serviços.</span><span class="sxs-lookup"><span data-stu-id="57445-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="57445-117">O `address`, `contract`, `contractNamespace`, `binding` e `bindingNamespace` parâmetros são usados para identificar o serviço pretendido.</span><span class="sxs-lookup"><span data-stu-id="57445-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="57445-118">Depois que esses parâmetros de correspondência, o moniker constrói um cliente do WCF com a definição de contrato apropriado e possível, em seguida, fazer chamadas usando o cliente do WCF, assim como acontece com o contrato com tipo.</span><span class="sxs-lookup"><span data-stu-id="57445-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57445-119">Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="57445-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="57445-120">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="57445-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57445-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57445-121">See also</span></span>

- [<span data-ttu-id="57445-122">Como: Registrar e configurar um Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="57445-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
