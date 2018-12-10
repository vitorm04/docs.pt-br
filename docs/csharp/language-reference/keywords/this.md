---
title: Palavra-chave this (Referência de C#)
description: Palavra-chave this (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130803"
---
# <a name="this-c-reference"></a>this (Referência de C#)

A palavra-chave `this` refere-se à instância atual da classe e também é usada como um modificador do primeiro parâmetro de um método de extensão.

> [!NOTE]
> Este artigo discute o uso de `this` com instâncias de classe. Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

Veja a seguir usos comuns de `this`:

- Para qualificar membros ocultados por nomes semelhantes, por exemplo:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Para passar um objeto como parâmetro para outros métodos, por exemplo:

  ```csharp
  CalcTax(this);
  ```

- Para declarar indexadores, por exemplo:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Funções de membro estático, por existirem no nível da classe e não como parte de um objeto, não têm um ponteiro `this`. É um erro se referir a `this` em um método estático.

## <a name="example"></a>Exemplo

Neste exemplo, `this` é usado para qualificar os membros de classe `Employee`, `name` e `alias`, que são ocultados por nomes semelhantes. Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [base](base.md)
- [Métodos](../../programming-guide/classes-and-structs/methods.md)
