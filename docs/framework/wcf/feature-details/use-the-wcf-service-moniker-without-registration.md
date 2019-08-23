---
title: 'Como: usar o moniker de serviço do Windows Communication Foundation sem registro'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: 16f428b614fe331faffabab477c6584fb682801d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955241"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="1fc96-102">Como: usar o moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="1fc96-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="1fc96-103">Para se conectar e se comunicar com um serviço Windows Communication Foundation (WCF), um aplicativo cliente WCF deve ter os detalhes do endereço de serviço, a configuração de associação e o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="1fc96-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="1fc96-104">O moniker do serviço WCF normalmente Obtém o contrato necessário por meio do registro anterior dos tipos de atributo necessários, mas pode haver casos em que isso não é viável.</span><span class="sxs-lookup"><span data-stu-id="1fc96-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="1fc96-105">No lugar do registro, o moniker pode obter a definição do contrato na forma de um documento WSDL (Web Services Definition Language), por meio do uso do `wsdl` parâmetro ou da troca de metadados, por meio do uso do `mexAddress` meter.</span><span class="sxs-lookup"><span data-stu-id="1fc96-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="1fc96-106">Isso permite cenários como a distribuição de uma planilha do Excel em que alguns dos valores de célula são calculados por meio de interações de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="1fc96-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="1fc96-107">Nesse cenário, talvez não seja possível registrar o assembly do contrato de serviço em todos os clientes que possam abrir o documento.</span><span class="sxs-lookup"><span data-stu-id="1fc96-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="1fc96-108">O `wsdl` parâmetro ou o `mexAddress` parâmetro habilita uma solução independente.</span><span class="sxs-lookup"><span data-stu-id="1fc96-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fc96-109">A autenticação mútua deve ser usada para proteger contra violação ou falsificação de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="1fc96-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="1fc96-110">Especificamente, é importante que os clientes tenham certeza de que o ponto de extremidade de troca de metadados que está respondendo é a parte confiável pretendida.</span><span class="sxs-lookup"><span data-stu-id="1fc96-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fc96-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fc96-111">Example</span></span>  
 <span data-ttu-id="1fc96-112">Este exemplo mostra o uso do moniker de serviço com um contrato MEX.</span><span class="sxs-lookup"><span data-stu-id="1fc96-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="1fc96-113">Um serviço com o contrato a seguir é exposto com uma wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="1fc96-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
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
  
 <span data-ttu-id="1fc96-114">Para construir um cliente WCF para o serviço remoto, o seguinte exemplo de cadeia de caracteres do moniker pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="1fc96-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="1fc96-115">Durante a execução do aplicativo cliente, o cliente executa um `WS-MetadataExchange` com o fornecido. `mexAddress`</span><span class="sxs-lookup"><span data-stu-id="1fc96-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="1fc96-116">Isso pode retornar os detalhes de endereço, associação e contrato para vários serviços.</span><span class="sxs-lookup"><span data-stu-id="1fc96-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="1fc96-117">Os `address` parâmetros`bindingNamespace` , `contract`, esãousadosparaidentificaroserviçopretendido.`binding` `contractNamespace`</span><span class="sxs-lookup"><span data-stu-id="1fc96-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="1fc96-118">Depois que esses parâmetros forem correspondidos, o moniker construirá um cliente WCF com a definição de contrato apropriada e as chamadas poderão ser feitas usando o cliente WCF, como com o contrato tipado.</span><span class="sxs-lookup"><span data-stu-id="1fc96-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fc96-119">Se o moniker estiver malformado ou se o serviço estiver indisponível, a `GetObject` chamada para retornará um erro dizendo "sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="1fc96-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="1fc96-120">Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="1fc96-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc96-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fc96-121">See also</span></span>

- [<span data-ttu-id="1fc96-122">Como: Registrar e configurar um moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="1fc96-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
