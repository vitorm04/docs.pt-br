---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12e9cbf5232ebbad33ccc4fdca33233997d27357
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371557"
---
# <a name="contract"></a>Contrato
Contrato  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de contrato não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe de contrato tem as seguintes propriedades:  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A id appdomain do appdomain que hospeda o contrato.  
  
### <a name="behaviors"></a>Comportamentos  
 Tipo de dados: matriz de comportamento  
  
 Tipo de acesso: somente leitura  
  
 Os comportamentos associados a esse contrato.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome do contrato em WSDL.  
  
### <a name="namespace"></a>Namespace  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O namespace do `portType` elemento no WSDL.  
  
### <a name="operations"></a>Operações  
 Tipo de dados: matriz de operação  
  
 Tipo de acesso: somente leitura  
  
 As operações do contrato.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O processo de identificação do processo que hospeda o contrato.  
  
### <a name="ref"></a>ref  
 Tipo de dados: contrato  
  
 Tipo de acesso: somente leitura  
  
 O tipo de retorno de chamada quando o contrato é um contrato duplex.  
  
### <a name="sessionmode"></a>SessionMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Indica se o contrato requer a associação associada a este contrato para usar sessões de canal.  
  
### <a name="type"></a>Tipo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O tipo do contrato.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ContractDescription>
