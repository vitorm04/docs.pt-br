---
title: O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)
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
 
