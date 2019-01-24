---
title: Valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691357"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)
Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido a combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'. Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas as referências são do mesmo local.  
  
 Em uma situação em que um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo pode ser convertido para outro.  
  
 Cada referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL). O compilador não pode garantir que os arquivos de saída provenientes da mesma fonte ou que eles representam a mesma versão do mesmo assembly. Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo, ou que um deles pode ser convertido para outro.  
  
 Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único. O *identidade de assembly* inclui nome, versão, se houver de chave pública e cultura do assembly. Essas informações identificam exclusivamente o assembly.  
  
 **ID do erro:** BC30961  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se os assemblies referenciados tiverem a mesma identidade de assembly, em seguida, remover ou substituir uma das referências de arquivo para que haja apenas uma referência de arquivo único.  
  
-   Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tenta converter um tipo em um a um tipo em outro.  
  
## <a name="see-also"></a>Consulte também
- [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)

