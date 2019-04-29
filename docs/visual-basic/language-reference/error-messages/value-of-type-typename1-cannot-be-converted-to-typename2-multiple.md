---
title: O valor do tipo '<typename1>' não pode ser convertido em '<typename2>' (várias referências ao arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766812"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >' (várias referências de arquivo)
Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido a combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'. Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas as referências são do mesmo local.  
  
 Em uma situação em que um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo pode ser convertido para outro.  
  
 Cada referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL). O compilador não pode garantir que os arquivos de saída provenientes da mesma fonte ou que eles representam a mesma versão do mesmo assembly. Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo, ou que um deles pode ser convertido para outro.  
  
 Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único. O *identidade de assembly* inclui nome, versão, se houver de chave pública e cultura do assembly. Essas informações identificam exclusivamente o assembly.  
  
 **ID do erro:** BC30961  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se os assemblies referenciados tiverem a mesma identidade de assembly, em seguida, remover ou substituir uma das referências de arquivo para que haja apenas uma referência de arquivo único.  
  
- Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tenta converter um tipo em um a um tipo em outro.  
  
## <a name="see-also"></a>Consulte também

- [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
