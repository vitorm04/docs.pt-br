---
title: Serviço
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196902"
---
# <a name="service"></a>Serviço
Serviço  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de serviço não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe de serviço tem as seguintes propriedades:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Os endereços base usados pelo serviço.  
  
### <a name="behaviors"></a>Comportamentos  
 Tipo de dados: matriz de comportamento  
  
 Tipo de acesso: somente leitura  
  
 Os comportamentos associados a esse serviço.  
  
### <a name="configurationname"></a>ConfigurationName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Nome da instância da instância dos contadores de desempenho do serviço.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Nome do serviço no endereço.  
  
### <a name="extensions"></a>Extensões  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Os contextos de instância para as extensões da instância do serviço.  
  
### <a name="metadata"></a>Metadados  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 As definições de metadados de serviço.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome exclusivo deste serviço.  
  
### <a name="namespace"></a>Namespace  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O namespace do serviço.  
  
### <a name="opened"></a>Aberto  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 A hora em que o serviço foi aberto.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Tipo de dados: matriz de canal  
  
 Tipo de acesso: somente leitura  
  
 Os canais que estão saindo da instância do serviço.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A id do processo do processo que hospeda o serviço.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|
