---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165446"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe MustUnderstandBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe MustUnderstandBehavior tem a seguinte propriedade:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
