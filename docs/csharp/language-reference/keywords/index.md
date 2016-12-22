---
title: "Palavras-chave C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.keywords"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave @"
  - "Linguagem C#, palavras-chave"
  - "palavras-chave [C#]"
  - "Visual C#, palavras-chave"
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Palavras-chave C# #
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Palavras\-chave são identificadores predefinidos e reservados, que têm significado especial para o compilador.  Eles não podem ser usados como identificadores em seu programa a menos que incluam `@` como um prefixo.  Por exemplo, `@if` é um identificador válido, mas `if` não é porque `if` é uma palavra\-chave.  
  
 A primeira tabela neste tópico lista palavras\-chave que são identificadores reservados em qualquer parte de um programa C\#.  A segunda tabela neste tópico lista palavras\-chave contextuais em C\#.  Palavras\-chave contextuais tem significado especial somente em um limitado contexto do programa e podem ser usadas como identificadores fora desse contexto.  Geralmente, quando novas Palavras\-chave são adicionadas à linguagem C\#, elas são adicionadas como palavras\-chave contextuais para evitar danos em programas escritos em versões anteriores.  
  
|||||  
|-|-|-|-|  
|[abstrata](../../../csharp/language-reference/keywords/abstract.md)|[Como](../../../csharp/language-reference/keywords/as.md)|[Base](../../../csharp/language-reference/keywords/base.md)|[bool](../../../csharp/language-reference/keywords/bool.md)|  
|[Quebra](../../../csharp/language-reference/keywords/break.md)|[Byte](../../../csharp/language-reference/keywords/byte.md)|[Caso](../../../csharp/language-reference/keywords/switch.md)|[Capturar](../../../csharp/language-reference/keywords/try-catch.md)|  
|[char](../../../csharp/language-reference/keywords/char.md)|[Marcada](../../../csharp/language-reference/keywords/checked.md)|[classe](../../../csharp/language-reference/keywords/class.md)|[Const](../../../csharp/language-reference/keywords/const.md)|  
|[Continuar](../../../csharp/language-reference/keywords/continue.md)|[decimal](../../../csharp/language-reference/keywords/decimal.md)|[Padrão](../../../csharp/language-reference/keywords/default.md)|[delegado](../../../csharp/language-reference/keywords/delegate.md)|  
|[Fazer](../../../csharp/language-reference/keywords/do.md)|[double](../../../csharp/language-reference/keywords/double.md)|[Pessoa](../../../csharp/language-reference/keywords/if-else.md)|[Enum](../../../csharp/language-reference/keywords/enum.md)|  
|[Evento](../../../csharp/language-reference/keywords/event.md)|[explícitas](../../../csharp/language-reference/keywords/explicit.md)|[extern](../../../csharp/language-reference/keywords/extern.md)|[FALSO](../../../csharp/language-reference/keywords/false.md)|  
|[Finalmente](../../../csharp/language-reference/keywords/try-finally.md)|[Fixo](../../../csharp/language-reference/keywords/fixed-statement.md)|[float](../../../csharp/language-reference/keywords/float.md)|[Para](../../../csharp/language-reference/keywords/for.md)|  
|[foreach](../../../csharp/language-reference/keywords/foreach-in.md)|[goto](../../../csharp/language-reference/keywords/goto.md)|[Se](../../../csharp/language-reference/keywords/if-else.md)|[implícito](../../../csharp/language-reference/keywords/implicit.md)|  
|[Em](../../../csharp/language-reference/keywords/foreach-in.md)|[em \(modificador genérico\)](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)|[int](../../../csharp/language-reference/keywords/int.md)|[interface](../../../csharp/language-reference/keywords/interface.md)|  
|[interno](../../../csharp/language-reference/keywords/internal.md)|[é](../../../csharp/language-reference/keywords/is.md)|[Bloqueio](../../../csharp/language-reference/keywords/lock-statement.md)|[long](../../../csharp/language-reference/keywords/long.md)|  
|[namespace](../../../csharp/language-reference/keywords/namespace.md)|[Novo](../../../csharp/language-reference/keywords/new.md)|[Nulo](../../../csharp/language-reference/keywords/null.md)|[object](../../../csharp/language-reference/keywords/object.md)|  
|[Operador](../../../csharp/language-reference/keywords/operator.md)|[Limite](../../../csharp/language-reference/keywords/out.md)|[check\-out \(modificador genérico\)](../../../csharp/language-reference/keywords/out-generic-modifier.md)|[override](../../../csharp/language-reference/keywords/override.md)|  
|[Parâmetros](../../../csharp/language-reference/keywords/params.md)|[Particular](../../../csharp/language-reference/keywords/private.md)|[Protegido](../../../csharp/language-reference/keywords/protected.md)|[Público](../../../csharp/language-reference/keywords/public.md)|  
|[readonly](../../../csharp/language-reference/keywords/readonly.md)|[Ref](../../../csharp/language-reference/keywords/ref.md)|[Retornar](../../../csharp/language-reference/keywords/return.md)|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|  
|[autenticada](../../../csharp/language-reference/keywords/sealed.md)|[short](../../../csharp/language-reference/keywords/short.md)|[sizeof](../../../csharp/language-reference/keywords/sizeof.md)|[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)|  
|[estático](../../../csharp/language-reference/keywords/static.md)|[string](../../../csharp/language-reference/keywords/string.md)|[struct](../../../csharp/language-reference/keywords/struct.md)|[Alternar](../../../csharp/language-reference/keywords/switch.md)|  
|[Isso](../../../csharp/language-reference/keywords/this.md)|[Descartar](../../../csharp/language-reference/keywords/throw.md)|[verdadeiro](../../../csharp/language-reference/keywords/true.md)|[Tente](../../../csharp/language-reference/keywords/try-catch.md)|  
|[TypeOf](../../../csharp/language-reference/keywords/typeof.md)|[uint](../../../csharp/language-reference/keywords/uint.md)|[ulong](../../../csharp/language-reference/keywords/ulong.md)|[desmarcada](../../../csharp/language-reference/keywords/unchecked.md)|  
|[Não seguro](../../../csharp/language-reference/keywords/unsafe.md)|[ushort](../../../csharp/language-reference/keywords/ushort.md)|[Usando](../../../csharp/language-reference/keywords/using.md)|[virtual](../../../csharp/language-reference/keywords/virtual.md)|  
|[Void](../../../csharp/language-reference/keywords/void.md)|[volátil](../../../csharp/language-reference/keywords/volatile.md)|[Tempo](../../../csharp/language-reference/keywords/while.md)||  
  
## Palavras\-chave contextuais  
 Um palavra\-chave contextual é usada para fornecer um determinado significado no código, mas ela não é uma palavra reservada em C\#.  Algumas palavras\-chave contextual, como `partial` e `where`, têm um significado especial em dois ou mais contextos.  
  
||||  
|-|-|-|  
|[Adicionar](../../../csharp/language-reference/keywords/add.md)|[alias](../../../csharp/language-reference/keywords/extern-alias.md)|[em ordem crescente](../../../csharp/language-reference/keywords/ascending.md)|  
|[Async](../../../visual-basic/language-reference/modifiers/async.md)|[aguardar](../../../csharp/language-reference/keywords/await.md)|[em ordem decrescente](../../../csharp/language-reference/keywords/descending.md)|  
|[dinâmico](../../../csharp/language-reference/keywords/dynamic.md)|[de](../../../visual-basic/language-reference/queries/from-clause.md)|[Obter](../../../csharp/language-reference/keywords/get.md)|  
|[global](../../../csharp/language-reference/keywords/global.md)|[group](../../../csharp/language-reference/keywords/group-clause.md)|[em](../../../csharp/language-reference/keywords/into.md)|  
|[associação](../../../csharp/language-reference/keywords/join-clause.md)|[Let](../../../csharp/language-reference/keywords/let-clause.md)|[OrderBy](../../../csharp/language-reference/keywords/orderby-clause.md)|  
|[parcial \(tipo\)](../../../csharp/language-reference/keywords/partial-type.md)|[parcial \(método\)](../../../csharp/language-reference/keywords/partial-method.md)|[remover](../../../csharp/language-reference/keywords/remove.md)|  
|[Selecione](../../../csharp/language-reference/keywords/select-clause.md)|[Definir](../../../csharp/language-reference/keywords/set.md)|[Valor](../../../csharp/language-reference/keywords/value.md)|  
|[var](../../../csharp/language-reference/keywords/var.md)|[onde \(restrição de tipo genérico\)](../../../csharp/language-reference/keywords/where-generic-type-constraint.md)|[onde \(cláusula de consulta\)](../../../visual-basic/language-reference/queries/where-clause.md)|  
|[Produzir](../../../csharp/language-reference/keywords/yield.md)||  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)