---
title: Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;objeto&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641122"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;objeto&#39;
O `FilePut` método inclui um argumento do tipo `Object`. `FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Substitua `FilePut` por `FilePutObject`.  
  
-   Conversão de `Object` argumento para um tipo mais específico.  
  
-   Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
