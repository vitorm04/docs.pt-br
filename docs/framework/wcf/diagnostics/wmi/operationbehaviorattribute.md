---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 6266713307846ab953299370835726958196fac1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185333"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
 A classe OperationBehaviorAttribute não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe OperationBehaviorAttribute tem as seguintes propriedades:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 O estado do recurso auto-dispose para parâmetros.  
  
### <a name="impersonation"></a>Representação  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Indica o nível de representação do chamador com suporte pela operação.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Indica quando no decorrer de uma invocação de operação para reciclar o objeto.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se é necessário confirmar a transação atual automaticamente se não ocorrer nenhuma exceção sem tratamento.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se a operação requer uma transação.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
