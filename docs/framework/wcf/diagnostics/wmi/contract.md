---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12b45c08a3d8dc69e740ce77d0d2abd097907ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="contract"></a>Contrato
Contrato  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe de contrato não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe de contrato tem as seguintes propriedades:  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A identificação appdomain do appdomain que hospeda o contrato.  
  
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
  
 O namespace do `portType` elemento em WSDL.  
  
### <a name="operations"></a>Operações  
 Tipo de dados: matriz de operação  
  
 Tipo de acesso: somente leitura  
  
 As operações desse contrato.  
  
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
  
 Indica se o contrato requer a associação associada a esse contrato use sessões do canal.  
  
### <a name="type"></a>Tipo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O tipo do contrato.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ContractDescription>
