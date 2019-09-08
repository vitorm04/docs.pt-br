---
title: Ponto de extremidade
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795900"
---
# <a name="endpoint"></a>Ponto de extremidade
Ponto de extremidade  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe Endpoint define o método a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](getoperationcounterinstancename.md)|Recupera o nome da instância do contador de desempenho da operação|  
  
## <a name="properties"></a>Propriedades  
 A classe de ponto de extremidade tem as seguintes propriedades:  
  
### <a name="address"></a>Endereço  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um URI que contém o endereço do ponto de extremidade.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A coleção de cabeçalhos de endereço anexado a este ponto de extremidade.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A identidade do ponto de extremidade.  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A ID de AppDomain do AppDomain que hospeda o ponto de extremidade.  
  
### <a name="behaviors"></a>Comportamentos  
 Tipo de dados: Matriz de comportamento  
  
 Tipo de acesso: Somente leitura  
  
 A coleção de comportamentos implementados por esse ponto de extremidade.  
  
### <a name="binding"></a>Associação  
 Tipo de dados: Associação  
  
 Tipo de acesso: Somente leitura  
  
 A associação usada por esse ponto de extremidade.  
  
### <a name="contractname"></a>ContractName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Uma cadeia de caracteres que especifica qual contrato esse ponto de extremidade está expondo.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O nome da instância de contadores de desempenho do ponto de extremidade.  
  
### <a name="listenuri"></a>ListenUri  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O URI no qual o ponto de extremidade escuta.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O nome exclusivo deste ponto de extremidade.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A ID do processo do processo que hospeda o ponto de extremidade.  
  
### <a name="ref"></a>ref  
 Tipo de dados: Contrato  
  
 Tipo de acesso: Somente leitura  
  
 O contrato que esse ponto de extremidade está expondo.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em ServiceModel. mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
