---
title: Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;objeto&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;objeto&#39;
O `FileGet` método inclui um argumento do tipo `Object`. `FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.  
  
 Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Substitua `FileGet` por `FileGetObject`.  
  
2.  Conversão de `Object` argumento para um tipo mais específico.  
  
## <a name="see-also"></a>Consulte também  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
