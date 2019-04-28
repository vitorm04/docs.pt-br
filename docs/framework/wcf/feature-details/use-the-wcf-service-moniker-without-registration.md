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
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Como: usar o moniker de serviço do Windows Communication Foundation sem registro
Para conectar e se comunicar com um serviço do Windows Communication Foundation (WCF), um aplicativo de cliente do WCF deve ter os detalhes do contrato de serviço, a configuração de associação e o endereço do serviço.  
  
 Geralmente, o moniker de serviço do WCF obtém o contrato exigido por meio do registro anterior dos tipos de atributo necessário, mas pode haver casos em que isso não é viável. No lugar do registro, o moniker pode obter a definição do contrato na forma de um documento WSDL Web Services Definition Language (), com o uso do `wsdl` parâmetro ou por meio da troca de metadados, através do uso do `mexAddress` parâmetro.  
  
 Isso permite cenários como a distribuição de uma planilha do Excel em que alguns dos valores de célula são calculados por meio de interações de serviço Web. Nesse cenário, talvez não seja viável para registrar o assembly do contrato de serviço em todos os clientes que podem abrir o documento. O `wsdl` parâmetro ou o `mexAddress` parâmetro permite que uma solução independente.  
  
> [!NOTE]
>  A autenticação mútua deve ser usada para proteger contra a solicitação e resposta de falsificação ou adulteração. Especificamente, é importante para os clientes para ter certeza de que o ponto de extremidade de troca de metadados que está respondendo é a parte confiável desejado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra o uso do moniker de serviço com um contrato MEX. Um serviço com o seguinte contrato é exposto com wsHttpBinding.  
  
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
  
 Pode ser usado construir um cliente WCF para o serviço remoto a cadeia de caracteres de moniker de exemplo a seguir.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Durante a execução do aplicativo cliente, o cliente executa um `WS-MetadataExchange` fornecido `mexAddress`. Isso pode retornar o endereço, associação e detalhes do contrato para um número de serviços. O `address`, `contract`, `contractNamespace`, `binding` e `bindingNamespace` parâmetros são usados para identificar o serviço pretendido. Depois que esses parâmetros de correspondência, o moniker constrói um cliente do WCF com a definição de contrato apropriado e possível, em seguida, fazer chamadas usando o cliente do WCF, assim como acontece com o contrato com tipo.  
  
> [!NOTE]
>  Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida". Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
## <a name="see-also"></a>Consulte também

- [Como: Registrar e configurar um Moniker de serviço](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
