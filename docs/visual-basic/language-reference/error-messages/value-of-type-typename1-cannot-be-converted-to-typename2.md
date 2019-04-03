---
title: O valor do tipo '<typename1>' não pode ser convertido em '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829012"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'
Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido a combinação de uma referência de arquivo com uma referência de projeto ao assembly '\<assemblyname >'. Tente substituir a referência de arquivo para '\<filepath >' no projeto '\<projectname1 >' com uma referência de projeto a '\<projectname2 >'.  
  
 Em uma situação em que um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo pode ser convertido para outro.  
  
 O pseudocódigo a seguir ilustra uma situação que pode gerar esse erro.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projeto `P1` faz uma referência de projeto indireta por meio do projeto `P2` ao projeto `P3`e também uma referência para `P3`. A declaração de `commonObject` usa a referência de arquivo para `P3`, enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.  
  
 O problema nessa situação é que a referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de `P3` (geralmente p3. dll), enquanto as referências do projeto identificam o projeto de origem (`P3`) pelo nome do projeto. Por isso, o compilador não pode garantir que o tipo `P3.commonClass` vem do mesmo código-fonte por meio de duas referências diferentes.  
  
 Essa situação normalmente ocorre quando as referências de projeto e referências de arquivo são misturadas. Na ilustração anterior, o problema não ocorrerá se `P1` feita uma referência direta ao `P3` em vez de uma referência de arquivo.  
  
 **ID do erro:** BC30955  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere a referência de arquivo para uma referência de projeto.  
  
## <a name="see-also"></a>Consulte também

- [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
