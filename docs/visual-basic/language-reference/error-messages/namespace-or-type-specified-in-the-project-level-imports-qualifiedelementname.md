---
title: "O namespace ou o tipo especificado no n&#237;vel de projeto Imports &#39;&lt;qualifiedelementname&gt;&#39; n&#227;o cont&#233;m nenhum membro p&#250;blico ou n&#227;o pode ser localizado. | Microsoft Docs"
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
  - "vbc40057"
  - "bc40057"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40057"
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O namespace ou o tipo especificado no n&#237;vel de projeto Imports &#39;&lt;qualifiedelementname&gt;&#39; n&#227;o cont&#233;m nenhum membro p&#250;blico ou n&#227;o pode ser localizado.
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Namespace ou tipo especificado em Imports de nível de projeto '\<qualifiedelementname\> ' não contém nenhum membro público ou não foi encontrado.Certifique\-se que o namespace ou o tipo está definido e contém apenas um membro público.Certifique\-se que o nome do alias não contem outros alias  
  
 Uma propriedade de importação de um projeto especifica um elemento contido que ou não pode ser achado ou não define nenhum membro `Public` .  
  
 Um *elemento contido* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.  O elemento contido contém membros, além de variáveis, procedimentos ou outros elementos contidos.  
  
 O propósito de importar é permitir seu código a acessar namespace ou digitar membros sem ter que qualificá\-los.  Seu projeto pode precisar também de adicionar uma referência ao namespace ou ao tipo.  Para mais informação veja "Importing Containing Elements" in [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não puder achar o elemento contido, então ele não pode resolver referências que o usam;.  Se ele acha o elemento mas o elemento não expõe nenhum membro  `Public`, então nenhuma referência pode ser bem\-sucedida.  Em ambos os casos é sem\-sentido importar o elemento.  
  
 Você usa o  **Project Designer**para especificar elementos a importar.  Use a seção **Imported namespaces** da página **References**.  Abra o  **Project Designer**  clicando duas vezes no ícone  **Meu projeto**  no  **Gerenciador de Soluções** .  
  
 **Identificação do Erro:**BC30415  
  
### Para corrigir este erro  
  
1.  Abra o **Designer de Projeto** e abra a página **Referência**.  
  
2.  Na seção **Namespaces importados**, verifique o elemento contêiner está acessível do seu projeto.  
  
3.  Verifique que o elemento contêiner expõe pelo um membro `Public`.  
  
## Consulte também  
 [Página Referências, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)