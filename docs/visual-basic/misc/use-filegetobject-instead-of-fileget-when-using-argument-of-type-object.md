---
title: Usar &#39; FileGetObject &#39; em vez de &#39; FileGet &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Usar &#39; FileGetObject &#39; em vez de &#39; FileGet &#39; Quando usar argumento do tipo &#39; objeto &#39;
O `FileGet` método inclui um argumento do tipo `Object`. `FileGetObject`deve ser usado no lugar de `FileGet` para evitar ambiguidades.  
  
 Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Substitua `FileGet` por `FileGetObject`.  
  
2.  Conversão de `Object` argumento para um tipo mais específico.  
  
## <a name="see-also"></a>Consulte também  
   
 [FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
