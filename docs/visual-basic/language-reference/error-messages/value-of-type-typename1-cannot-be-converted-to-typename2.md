---
title: O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 9b3c029ed7bf73ff92dba65438d797b27fa135f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt;&#39;
O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode se dever à combinação de uma referência de arquivo com uma referência ao assembly '\<assemblyname >'. Tente substituir a referência de arquivo para '\<filepath >' no projeto '\<projectname1 >' com uma referência de projeto para '\<projectname2 >'.  
  
 Em uma situação na qual um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo possa ser convertido para outro.  
  
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
  
 Projeto `P1` faz uma referência indireta projeto por meio do projeto `P2` ao projeto `P3`e também uma referência a `P3`. A declaração de `commonObject` usa a referência de arquivo para `P3`, enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.  
  
 O problema nessa situação é que a referência do arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída do `P3` (geralmente p3. dll), enquanto as referências do projeto identificam o projeto de origem (`P3`) pelo nome do projeto. Por isso, o compilador não pode garantir que o tipo `P3.commonClass` vêm do mesmo código-fonte por meio de duas referências diferentes.  
  
 Essa situação normalmente ocorre quando as referências do projeto e as referências do arquivo estão misturadas. Na ilustração anterior, o problema não ocorrerá se `P1` feita uma referência direta ao `P3` em vez de uma referência de arquivo.  
  
 **ID do erro:** BC30955  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere a referência de arquivo para uma referência de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)  
 
