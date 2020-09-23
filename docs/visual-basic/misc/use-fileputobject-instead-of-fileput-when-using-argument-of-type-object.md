---
title: Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100328"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'

O `FilePut` método inclui um argumento do tipo `Object` . `FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Substitua `FilePut` por `FilePutObject`.  
  
- Converta o `Object` argumento para um tipo mais específico.  
  
- Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Confira também

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My. Computer. FileSystem. WriteAllBytesAsyncInternal](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
