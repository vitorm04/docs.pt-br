---
title: "Refer&#234;ncia necess&#225;ria para o assembly &#39;&lt; assemblyidentity &gt;&#39; contendo o tipo &#39;&lt; typename &gt;&#39;, mas uma refer&#234;ncia adequada n&#227;o p&#244;de ser encontrado devido &#224; ambiguidade entre os projetos &#39;&lt; projectname1 &gt;&#39; e &#39;&lt; projectname2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30969"
  - "vbc30969"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30969"
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia necess&#225;ria para o assembly &#39;&lt; assemblyidentity &gt;&#39; contendo o tipo &#39;&lt; typename &gt;&#39;, mas uma refer&#234;ncia adequada n&#227;o p&#244;de ser encontrado devido &#224; ambiguidade entre os projetos &#39;&lt; projectname1 &gt;&#39; e &#39;&lt; projectname2 &gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora do seu projeto. No entanto, você tem referências do projeto a mais de um assembly definindo o tipo.  
  
 Os projetos citados produzem assemblies com o mesmo nome. Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.  
  
 Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não cause referências circulares entre projetos.  
  
 **ID do erro:** BC30969  
  
### Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso a arquivos e a freqüência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.  
  
## Consulte também  
 [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solucionando Problemas de Referências Quebradas](/visual-studio/ide/troubleshooting-broken-references)