---
title: "O valor do tipo &#39;&lt;typename1&gt;&#39; n&#227;o pode ser convertido em &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30955"
  - "bc30955"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30955"
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O valor do tipo &#39;&lt;typename1&gt;&#39; n&#227;o pode ser convertido em &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Valor do tipo '\<typename1\>' não pode ser convertido para '\<typename2\>'.A incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo com um referência de projeto para o conjunto de módulos \(assembly\) '\<assemblyname\>'.Tente substituir a referência de arquivo para '\<filepath\>' no projeto '\< projectname1 \>' com um referência de projeto para '\<projectname2\>'.  
  
 Numa situação na qual um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo possa ser convertido para outro.  
  
 O pseudo\-código a seguir ilustra uma situação que pode gerar esse erro.  
  
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
  
 Projeto `P1` faz um referência de projeto indireta através do projeto `P2` para o projeto `P3` e também uma referência a `P3` .  A declaração de `commonObject` usa a referência de arquivo para `P3`,enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.  
  
 O problema nessa situação é que a referência do arquivo especifica um caminho do arquivo e nome para o arquivo de saída de `P3` \(geralmente p3.dll\), enquanto que as referências do projeto identificam o projeto de origem \(`P3`\) pelo nome do projeto.  Devido a isso, o compilador não pode garantir que o tipo `P3.commonClass` vem do mesmo código\-fonte por meio de duas referências diferentes.  
  
 Essa situação geralmente ocorre quando as referências de projeto e referências do arquivo estão misturadas.  Na ilustração anterior, o problema não ocorreria se `P1` fez um referência de projeto para `P3` em vez de uma referência de arquivo.  
  
 **Identificação do erro:**  BC30955  
  
### Para corrigir este erro  
  
-   Altere a referência de arquivo para um referência de projeto.  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project)   
 [Como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)