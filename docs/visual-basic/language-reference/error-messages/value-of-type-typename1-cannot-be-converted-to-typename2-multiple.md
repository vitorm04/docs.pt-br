---
title: "Valor do tipo &#39; &lt;typename1&gt;&#39; não pode ser convertido para &#39;&lt; typename2&gt;&#39; (Várias referências de arquivo)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22516a5ca9626f43cb89745e67c66619cf9461f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Valor do tipo &#39; &lt;typename1&gt;&#39; não pode ser convertido para &#39;&lt; typename2&gt;&#39; (Várias referências de arquivo)
O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'. Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas sejam do mesmo local.  
  
 Em uma situação na qual um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo possa ser convertido para outro.  
  
 Cada referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL). O compilador não pode garantir que os arquivos de saída vêm da mesma origem, ou que eles representam a mesma versão do mesmo assembly. Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo ou que um deles pode ser convertido para o outro.  
  
 Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único. O *identidade de assembly* inclui nome, versão, chave pública, se houver e cultura do assembly. Essas informações identificam exclusivamente o assembly.  
  
 **ID do erro:** BC30961  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se os assemblies referenciados têm a mesma identidade de assembly, em seguida, remova ou substitua uma das referências de arquivo para que haja apenas uma referência de arquivo único.  
  
-   Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tentará converter um tipo em um tipo em outro.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)  
 
