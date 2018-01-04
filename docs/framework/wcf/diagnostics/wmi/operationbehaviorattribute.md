---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63824ae2171053bee2af204e748a6fa811f2ba82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe OperationBehaviorAttribute não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe OperationBehaviorAttribute tem as seguintes propriedades:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 O estado do recurso auto-dispose para parâmetros.  
  
### <a name="impersonation"></a>Representação  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Indica o nível de representação do chamador que a operação oferece suporte.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Indica quando no curso de uma invocação de operação reciclar o objeto.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se deve confirmar a transação atual automaticamente se nenhuma exceção não tratada ocorrer.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se a operação requer uma transação.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
