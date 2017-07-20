---
title: "this (Referência de C#) | Microsoft Docs"
description: "Palavra-chave this (Referência de C#)"
keywords: "this (C#), palavra-chave this (C#), palavra-chave this (referência de C#), palavra-chave this (referência da linguagem C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e14a32f11b9661ae18fd718fb1a72385fa7f3a7
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="this-c-reference"></a>this (Referência de C#)
A palavra-chave `this` refere-se à instância atual da classe e também é usada como um modificador do primeiro parâmetro de um método de extensão.  
  
> [!NOTE]
>  Este artigo discute o uso de `this` com instâncias de classe. Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Veja a seguir usos comuns de `this`:  
  
-   Para qualificar membros ocultados por nomes semelhantes, por exemplo:  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Para passar um objeto como parâmetro para outros métodos, por exemplo:  
  
    ```  
    CalcTax(this);  
    ```  
  
-   Para declarar indexadores, por exemplo:  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Funções de membro estático, por existirem no nível da classe e não como parte de um objeto, não têm um ponteiro `this`. É um erro se referir a `this` em um método estático.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `this` é usado para qualificar os membros de classe `Employee`, `name` e `alias`, que são ocultados por nomes semelhantes. Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)
