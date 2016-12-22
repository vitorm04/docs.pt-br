---
title: "Sem espa&#231;o na pilha (Visual Basic) | Microsoft Docs"
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
  - "vbrID28"
dev_langs: 
  - "VB"
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sem espa&#231;o na pilha (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A pilha é uma área de trabalho de memória que cresce e reduzida dinamicamente com as demandas de seu programa em execução.  Seus limites foram excedidos.  
  
### Para corrigir este erro  
  
1.  Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2.  Certifique\-se de procedimentos recursiva termine adequadamente.  
  
3.  Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarar algumas variáveis no nível de módulo.  Você pode também declarar todas as variáveis no procedimento estático precedendo a `Property`, `Sub`, ou `Function` palavra\-chave com `Static`.  Ou você pode usar o `Static` a instrução para declarar variáveis estáticas individuais dentro de procedimentos.  
  
4.  Redefina algumas das suas seqüências de comprimento fixo, como seqüências de caracteres de comprimento variável, como seqüências de comprimento fixo usam mais espaço de pilha que seqüências de caracteres de comprimento variável.  Você também pode definir a seqüência de caracteres no nível de módulo onde ele requer nenhum espaço de pilha.  
  
5.  Verificar o número de aninhadas `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo para exibir os procedimentos estão ativos na pilha.  
  
6.  Certifique\-se de que não cause "cascata de eventos" disparando um evento que chama um procedimento de evento já na pilha.  Cascata de eventos é semelhante a uma chamada de procedimento recursivo não finalizada, mas é menos óbvio, já que a chamada é feita por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] em vez de uma chamada explícita no código.  Use o `Calls` caixa de diálogo para exibir os procedimentos estão ativos na pilha.  
  
## Consulte também  
 [Janelas de memória](/visual-studio/debugger/memory-windows)