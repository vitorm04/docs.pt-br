---
title: "O valor do tipo &quot;&lt;typename1&gt;&quot;não pode ser convertido em&quot;&lt;typename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: c973d5e2aa03d423e1dea8053946172655f08490
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>O valor do tipo '&lt;typename1&gt;'não pode ser convertido em'&lt;typename2&gt;'
O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'. Incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo com uma referência ao assembly '\<assemblyname >'. Tente substituir a referência de arquivo para '\<filepath >' no projeto '\<projectname1 >' com uma referência de projeto para '\<projectname2 >'.  
  
 Em uma situação na qual um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo pode ser convertido para outro.  
  
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
  
 Projeto `P1` faz uma referência de projeto indireta através do projeto `P2` ao projeto `P3`e também uma referência a `P3`. A declaração de `commonObject` usa a referência de arquivo para `P3`, enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.  
  
 O problema nessa situação é que a referência do arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de `P3` (geralmente p3. dll), enquanto as referências do projeto identificam o projeto de origem (`P3`) pelo nome do projeto. Por isso, o compilador não pode garantir que o tipo `P3.commonClass` vem do mesmo código-fonte por meio de duas referências diferentes.  
  
 Essa situação normalmente ocorre quando as referências de projeto e referências de arquivo são misturadas. Na ilustração anterior, o problema não ocorreria se `P1` feita uma referência direta ao `P3` em vez de uma referência de arquivo.  
  
 **ID do erro:** BC30955  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere a referência de arquivo para uma referência de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
