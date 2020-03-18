---
title: Reflexão (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711669"
---
# <a name="reflection-c"></a>Reflexão (C#)

A reflexão fornece <xref:System.Type>objetos (de tipo) que descrevem conjuntos, módulos e tipos. É possível usar a reflexão para criar dinamicamente uma instância de um tipo, associar o tipo a um objeto existente ou obter o tipo de um objeto existente e invocar seus métodos ou acessar suas propriedades e campos. Se você estiver usando atributos em seu código, a reflexão permite acessá-los. Para obter mais informações, consulte [Atributos](../../../standard/attributes/index.md).

Aqui está um exemplo simples <xref:System.Object.GetType> de reflexão usando o `Object` método - herdado por todos os tipos da classe base - para obter o tipo de variável:

> [!NOTE]
> Certifique-se `using System;` de `using System.Reflection;` adicionar e na parte superior do seu arquivo *.cs.*

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

A saída `System.Int32`é: .

O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

A saída `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`é: .

> [!NOTE]
> As palavras-chave de C# `protected` e `internal` não têm significado no IL e não são usadas nas APIs de reflexão. Os termos correspondentes na IL são *Família* e *Assembly*. Para identificar um método `internal` usando a reflexão, use a propriedade <xref:System.Reflection.MethodBase.IsAssembly%2A>. Para identificar um método `protected internal`, use o <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Visão geral da reflexão

A reflexão é útil nas seguintes situações:

- Quando você precisa acessar atributos nos metadados do seu programa. Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Para examinar e instanciar tipos em um assembly.
- Para criar novos tipos em runtime. Usar as classes em <xref:System.Reflection.Emit>.
- Para executar a associação tardia, acessar métodos em tipos criados em tempo de execução. Consulte o tópico [Carregando e usando tipos dinamicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Seções relacionadas

Para mais informações:

- [Reflexão](../../../framework/reflection-and-codedom/reflection.md)
- [Exibindo informações de tipo](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Reflexão e tipos genéricos](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Assemblies no .NET](../../../standard/assembly/index.md)
