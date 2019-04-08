---
title: Integração com visão geral de aplicativos COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 182e5f41498d8f5e3fcbc4b84aa7e86b67ce3ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087619"
---
# <a name="integrating-with-com-applications-overview"></a>Integração com visão geral de aplicativos COM
Windows Communication Foundation (WCF) oferece ao desenvolvedor de código gerenciado com um ambiente rico para a criação de aplicativos conectados. No entanto, se você tiver um investimento substancial em código não gerenciado COM base em com e não deseja migrar, você pode ainda integrar os serviços Web WCF diretamente em seu código existente usando o moniker de serviço do WCF. O moniker de serviço pode ser usado em ambientes um amplo intervalo de COM base em desenvolvimento, como Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.  
  
> [!NOTE]
>  O moniker de serviço usa um canal de comunicação do WCF para toda a comunicação. Os mecanismos de segurança e identidade para esse canal diferem daqueles usados no padrão proxies COM e DCOM. Além disso, como o moniker de serviço usa um canal de comunicação WCF o período de tempo limite padrão é um minuto para todas as chamadas.  
  
 O moniker de serviço é usado com o `GetObject` função para fornecer o desenvolvedor não gerenciado com uma abordagem fortemente tipada COM específicas para chamar serviços Web WCF. Isso requer um local, a definição visível do contrato de serviço Web WCF e a associação a ser usado. Como outros clientes do WCF, o moniker de serviço deve construir um canal tipado para o serviço, embora essa construção de canal ocorre de forma transparente para o programador COM na primeira chamada de método.  
  
 Em comum com outros clientes do WCF, ao usar o identificador de origem, os aplicativos especificam o endereço, ligação e contrato para se comunicar com um serviço. O contrato pode ser especificado em uma das seguintes maneiras:  
  
-   Contrato tipado – o contrato é registrado como um tipo visível do COM o computador cliente.  
  
-   Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.  
  
-   Contrato MEX – o contrato é recuperado em tempo de execução de um ponto de extremidade de troca de metadados (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parâmetros compatíveis com o Moniker de serviço  
 A tabela a seguir mostra os parâmetros que são compatíveis com o moniker de serviço.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`address`|Local da URL do serviço.|  
|`binding`|Associação de nome da seção de configuração do aplicativo.|  
|`bindingConfiguration`|Instância de ligação nomeada de dentro da seção de ligações nomeadas.|  
|`contract`|Identificador de interface (IID) que representa o contrato de serviço ou o nome do contrato (de MEX).|  
|`wsdl`|Documento WSDL que fornece uma forma alternativa de definição de contrato.|  
|`spnIdentity`|Identidade de nome da entidade (SPN) do servidor a ser usado para se comunicar com o serviço.|  
|`upnIdentity`|Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o serviço.|  
|`dnsIdentity`|Identidade do DNS a ser usado para se comunicar com o serviço.|  
|`mexAddress`|Local da URL do ponto de extremidade do serviço de troca de metadados (MEX).|  
|`mexBinding`|Associando o nome da seção de configuração do aplicativo para se conectar com o ponto de extremidade MEX.|  
|`mexBindingConfiguration`|Instância de ligação nomeada de dentro da seção de ligações nomeadas para se conectar com o ponto de extremidade MEX.|  
|`bindingNamespace`|Namespace do nome da seção de associação da MEX. recuperado|  
|`contractNamespace`|Namespace do contrato da MEX. recuperado|  
|`mexSpnIdentity`|Identidade de nome da entidade (SPN) do servidor a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`mexUpnIdentity`|Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`mexDnsIdentity`|Identidade do DNS a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`serializer`|Especifica o uso do serializador "xml" ou "datacontract".|  
  
> [!NOTE]
>  Mesmo quando usado com clientes inteiramente baseados em COM, o moniker de serviço requer o WCF e o suporte do .NET Framework 2.0 para ser instalado no computador cliente. Também é essencial que os aplicativos cliente que usam o moniker de serviço carregam a versão apropriada do runtime do .NET Framework. Ao usar o moniker em aplicativos do Office, um arquivo de configuração pode ser necessário para garantir que a versão do framework correto está carregada. Por exemplo, com o Excel, o texto a seguir deve ser colocado em um arquivo chamado exe no mesmo diretório que o arquivo Excel.exe:  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Consulte também

- [Como: registrar e configurar um moniker de serviço](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
