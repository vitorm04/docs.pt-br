---
title: "Integração com visão geral de aplicativos COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b20ae5329f08e9391fd7b93218c44c3c1978a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a>Integração com visão geral de aplicativos COM
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]oferece ao desenvolvedor de código gerenciado com um ambiente rico para criar aplicativos conectados. No entanto, se você tem um investimento significativo em código não gerenciado COM base em e não deseja migrar, você pode ainda integrar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços da Web diretamente no seu código existente usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker de serviço. O moniker de serviço pode ser usado em ambientes de desenvolvimento todo com base no intervalo de COM, como Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.  
  
> [!NOTE]
>  O moniker de serviço usa um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal de comunicação para todas as comunicações. Os mecanismos de segurança e identidade para esse canal diferem daqueles usados no padrão proxies COM e DCOM. Além disso, como o moniker de serviço usa um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal de comunicação, o período de tempo limite padrão é um minuto para todas as chamadas.  
  
 O moniker de serviço é usado com o `GetObject` função para fornecer o desenvolvedor não gerenciado com uma abordagem fortemente tipada COM específicas para chamar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços Web. Isso requer uma definição de local, COM visível do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web contrato de serviço e a associação a ser usado. Assim como outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, o moniker de serviço devem criar um canal inserido para o serviço, embora essa construção de canal ocorre de forma transparente para o programador COM na primeira chamada do método.  
  
 Em comum com outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, ao usar o moniker o aplicativos especificam o endereço, associação e contrato para se comunicar com um serviço. O contrato pode ser especificado em uma das seguintes maneiras:  
  
-   Contrato com tipo – o contrato é registrado como um tipo visível COM no computador cliente.  
  
-   Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.  
  
-   Contrato MEX – o contrato é recuperado em tempo de execução de um ponto de extremidade de troca de metadados (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parâmetros compatíveis com o Moniker de serviço  
 A tabela a seguir mostra os parâmetros que são suportados pelo moniker de serviço.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`address`|Local da URL do serviço.|  
|`binding`|Associação de nome da seção de configuração do aplicativo.|  
|`bindingConfiguration`|Instância nomeada de associação de dentro da seção de ligação nomeada.|  
|`contract`|Identificador de interface (IID) que representa o contrato de serviço ou o nome do contrato (de MEX).|  
|`wsdl`|Documento WSDL que fornece uma maneira alternativa de definição de contrato.|  
|`spnIdentity`|Identidade do servidor (SPN) nome da entidade a ser usado para se comunicar com o serviço.|  
|`upnIdentity`|Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o serviço.|  
|`dnsIdentity`|Identidade do DNS a ser usado para se comunicar com o serviço.|  
|`mexAddress`|Local da URL do ponto de extremidade do serviço de troca de metadados (MEX).|  
|`mexBinding`|Associação de nome de seção de configuração do aplicativo para se conectar com o ponto de extremidade MEX.|  
|`mexBindingConfiguration`|Instância nomeada de associação de dentro da seção de ligação nomeada para se conectar com o ponto de extremidade MEX.|  
|`bindingNamespace`|Namespace do nome da seção de associação do MEX. recuperados|  
|`contractNamespace`|Namespace do contrato do MEX. recuperados|  
|`mexSpnIdentity`|Identidade do servidor (SPN) nome da entidade a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`mexUpnIdentity`|Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`mexDnsIdentity`|Identidade do DNS a ser usado para se comunicar com o ponto de extremidade MEX.|  
|`serializer`|Especifique o uso do serializador de um "datacontract" ou "xml".|  
  
> [!NOTE]
>  Mesmo quando usado com clientes inteiramente baseados em COM, o moniker de serviço requer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e suporte do .NET Framework 2.0 para ser instalado no computador cliente. Também é importante que os aplicativos cliente que usam o moniker de serviço carregar a versão apropriada do tempo de execução do .NET Framework. Ao usar o moniker em aplicativos do Office, um arquivo de configuração pode ser necessário para garantir que a versão do framework correto seja carregada. Por exemplo, com o Excel, o texto a seguir deve ser colocado em um arquivo chamado Excel.exe.config no mesmo diretório que o arquivo Excel.exe:  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=``http://schemas.microsoft.com/.NetConfiguration/v2.0``>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Consulte também  
 [Como registrar e configurar um moniker de serviço](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
