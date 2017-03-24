---
title: "O valor do tipo &quot;&lt;typename1&gt;&quot;não pode ser convertido em&quot;&lt;typename2&gt;&quot; (várias referências de arquivo) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
dev_langs:
- VB
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 732291ce9c4b83bb9fc7e83fbbc2a8da9748db59
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>O valor do tipo '&lt;typename1&gt;'não pode ser convertido em'&lt;typename2&gt;' (várias referências de arquivo)
O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'. Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas sejam do mesmo local.  
  
 Em uma situação na qual um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo pode ser convertido para outro.  
  
 Cada referência do arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL). O compilador não pode garantir que os arquivos de saída vêm da mesma origem, ou que eles representam a mesma versão do mesmo assembly. Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo, ou que um deles pode ser convertido para outro.  
  
 Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único. O *identidade do assembly* inclui nome, versão, chave pública, se houver e cultura do assembly. Essa informação identifica unicamente o assembly.  
  
 **ID do erro:** BC30961  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se os assemblies referenciados têm a mesma identidade de assembly, remova ou substitua uma das referências de arquivo de forma que apenas uma referência de arquivo único.  
  
-   Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tentará converter um tipo em um tipo em outro.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
