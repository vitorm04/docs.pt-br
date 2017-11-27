---
title: Ponto de extremidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e27f6e7a45fe705aa09827702a64c960b6a16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint"></a>Ponto de extremidade
Ponto de extremidade  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe de ponto de extremidade define o método a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|Recupera o nome de instância do contador de desempenho de operação|  
  
## <a name="properties"></a>Propriedades  
 A classe de ponto de extremidade tem as seguintes propriedades:  
  
### <a name="address"></a>Endereço  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um URI que contém o endereço do ponto de extremidade.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A coleção de cabeçalhos de endereço anexados a esse ponto de extremidade.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A identidade do ponto de extremidade.  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A identificação appdomain do appdomain que hospeda o ponto de extremidade.  
  
### <a name="behaviors"></a>Comportamentos  
 Tipo de dados: matriz de comportamento  
  
 Tipo de acesso: somente leitura  
  
 A coleção de comportamentos implementados por esse ponto de extremidade.  
  
### <a name="binding"></a>Associação  
 Tipo de dados: associação  
  
 Tipo de acesso: somente leitura  
  
 A associação usada por esse ponto de extremidade.  
  
### <a name="contractname"></a>ContractName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Uma cadeia de caracteres que especifica qual contrato esse ponto de extremidade está expondo.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome da instância de contadores de desempenho do ponto de extremidade.  
  
### <a name="listenuri"></a>ListenUri  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O Uri do ponto de extremidade de escuta.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome exclusivo desse ponto de extremidade.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O processo de identificação do processo que hospeda o ponto de extremidade.  
  
### <a name="ref"></a>ref  
 Tipo de dados: contrato  
  
 Tipo de acesso: somente leitura  
  
 O contrato que esse ponto de extremidade está expondo.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
