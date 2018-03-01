---
title: Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
O `FilePut` método inclui um argumento do tipo `Object`. `FilePutObject`deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Substitua `FilePut` por `FilePutObject`.  
  
-   Conversão de `Object` argumento para um tipo mais específico.  
  
-   Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também  
   
 [FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
