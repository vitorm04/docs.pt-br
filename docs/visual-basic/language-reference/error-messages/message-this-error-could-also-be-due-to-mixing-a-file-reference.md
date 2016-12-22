---
title: "Esse erro tamb&#233;m pode ocorrer devido &#224; combina&#231;&#227;o de uma refer&#234;ncia de arquivo com uma refer&#234;ncia ao assembly &#39;&lt; assemblyname &gt;&#39; &lt; mensagem &gt; | Microsoft Docs"
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
  - "bc30971"
  - "vbc30971"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30971"
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esse erro tamb&#233;m pode ocorrer devido &#224; combina&#231;&#227;o de uma refer&#234;ncia de arquivo com uma refer&#234;ncia ao assembly &#39;&lt; assemblyname &gt;&#39; &lt; mensagem &gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\< Mensagem \> Esse erro também pode ocorrer devido à combinação de uma referência de arquivo com uma referência ao assembly ' \< assemblyname \>. Nesse caso, tente substituir a referência de arquivo para '\< assemblyfilename \>' no projeto '\< projectname1 \>' com uma referência de projeto para '\< projectname2 \>'.  
  
 Código no seu projeto acessa um membro de outro projeto, mas a configuração de sua solução não permite que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolver a referência.  
  
 Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não cause referências circulares entre projetos.  
  
 **ID do erro:** BC30971  
  
### Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso a arquivos e a freqüência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência ao projeto que contém o assembly que define o tipo que você está usando.  
  
## Consulte também  
 [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solucionando Problemas de Referências Quebradas](/visual-studio/ide/troubleshooting-broken-references)