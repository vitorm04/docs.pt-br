---
title: O valor do tipo '<typename1>' não pode ser convertido em '<typename2>' (várias referências ao arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 4b74fdc5584fd296d4bbe36034920d4b467dbb7a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875075"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>O valor do tipo '\<typename1>' não pode ser convertido em '\<typename2>' (várias referências ao arquivo)

O valor do tipo ' \<typename1> ' não pode ser convertido em ' \<typename2> '. A incompatibilidade de tipos pode ser devido à combinação de uma referência de arquivo para ' \<filepath1> ' no projeto ' \<projectname1> ' com uma referência de arquivo para ' \<filepath2> ' no projeto ' \<projectname2> '. Se ambos os assemblies forem idênticos, tente substituir essas referências para que ambas as referências sejam do mesmo local.  
  
 Em uma situação em que um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo possa ser convertido em outro.  
  
 Cada referência de arquivo especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (normalmente um arquivo DLL). O compilador não pode garantir que os arquivos de saída venham da mesma fonte, ou que eles representam a mesma versão do mesmo assembly. Portanto, ele não pode garantir que os tipos nas diferentes referências sejam do mesmo tipo, ou até mesmo que um deles possa ser convertido para o outro.  
  
 Você pode usar uma única referência de arquivo se souber que os assemblies referenciados têm a mesma identidade de assembly. A *identidade do assembly* inclui o nome do assembly, a versão, a chave pública, se houver, e a cultura. Essas informações identificam exclusivamente o assembly.  
  
 **ID do erro:** BC30961  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se os assemblies referenciados tiverem a mesma identidade de assembly, remova ou substitua uma das referências de arquivo para que haja apenas uma única referência de arquivo.  
  
- Se os assemblies referenciados não tiverem a mesma identidade de assembly, altere seu código para que ele não tente converter um tipo em um para um tipo no outro.  
  
## <a name="see-also"></a>Confira também

- [Conversões de tipo no Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
