---
title: "O namespace ou o tipo especificado em Imports &#39;&lt;qualifiedelementname&gt;&#39; n&#227;o cont&#233;m nenhum membro p&#250;blico ou n&#227;o pode ser localizado | Microsoft Docs"
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
  - "bc40056"
  - "vbc40056"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40056"
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O namespace ou o tipo especificado em Imports &#39;&lt;qualifiedelementname&gt;&#39; n&#227;o cont&#233;m nenhum membro p&#250;blico ou n&#227;o pode ser localizado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O namespace ou tipo especificado em Imports '\<qualifiedelementname\> ' não contém nenhum membro público ou não foi encontrado.Certifique\-se que o namespace ou o tipo está definido e contém apenas um membro público.Certifique\-se que o nome do alias não contem outros alias  
  
 Um `Imports` declaração especifica um elemento de recipiente que não pode ser encontrado ou não definir qualquer `Public` membros.  
  
 Um *elemento contido* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.  O elemento contido contém membros, além de variáveis, procedimentos ou outros elementos contidos.  
  
 O propósito de importar é permitir seu código a acessar namespace ou digitar membros sem ter que qualificá\-los.  Seu projeto pode precisar também de adicionar uma referência ao namespace ou ao tipo.  Para mais informação veja "Importing Containing Elements" in [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não puder achar o elemento contido, então ele não pode resolver referências que o usam;.  Se ele acha o elemento mas o elemento não expõe nenhum membro  `Public`, então nenhuma referência pode ser bem\-sucedida.  Em ambos os casos é sem\-sentido importar o elemento.  
  
 Tenha em mente que se você importar um elemento que contém e atribuir um alias de importação a ela, você não pode usar esse alias de importação para importar outro elemento.  O código a seguir gera um erro do compilador.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Identificação do erro:**  BC40056  
  
### Para corrigir este erro  
  
1.  Verifique se o elemento contido é acessível a partir de seu projeto.  
  
2.  Verifique se a especificação do elemento contido não incluem qualquer alias de importação na importação de outra.  
  
3.  Verifique que o elemento contêiner expõe pelo um membro `Public`.  
  
## Consulte também  
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)