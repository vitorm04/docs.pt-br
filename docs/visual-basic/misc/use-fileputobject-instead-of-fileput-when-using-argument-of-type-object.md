---
title: Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
O `FilePut` método inclui um argumento do tipo `Object`. `FilePutObject`deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Substitua `FilePut` por `FilePutObject`.  
  
-   Conversão de `Object` argumento para um tipo mais específico.  
  
-   Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [NÃO está em compilação: Função FilePutObject](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [Objeto My.Computer.FileSystem](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [Método WriteAllBytes](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
