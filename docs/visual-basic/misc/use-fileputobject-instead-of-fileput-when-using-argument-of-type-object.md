---
title: Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022513"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'
O `FilePut` método inclui um argumento do tipo `Object`. `FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Substitua `FilePut` por `FilePutObject`.  
  
- Conversão de `Object` argumento para um tipo mais específico.  
  
- Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
