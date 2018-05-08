---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe MustUnderstandBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe MustUnderstandBehavior tem a seguinte propriedade:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
