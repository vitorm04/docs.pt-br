---
title: Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022539"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'
O `FileGet` método inclui um argumento do tipo `Object`. `FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.  
  
 Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Substitua `FileGet` por `FileGetObject`.  
  
2. Conversão de `Object` argumento para um tipo mais específico.  
  
## <a name="see-also"></a>Consulte também

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
