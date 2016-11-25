---
title: Common Type System e Common Language Specification
description: Common Type System e Common Language Specification
keywords: .NET, .NET Core
author: blackdwarf
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
translationtype: Human Translation
ms.sourcegitcommit: 9cf6022fc910bc5418c03c0fa81d9432d85be3b0
ms.openlocfilehash: f655c141a0c86da7905091c138b7ec4324cad07a

---

# <a name="common-type-system-common-language-specification"></a>Common Type System e Common Language Specification

Novamente, dois termos que são usados livremente no mundo do .NET, eles realmente são essenciais para compreender como a plataforma do .NET permite o desenvolvimento para várias linguagens e para entender como ela funciona.

## <a name="common-type-system"></a>Common Type System

Para começar do zero, lembre-se de que a plataforma .NET é _independente de idioma_. Isso não significa apenas que um programador pode escrever seu código em qualquer idioma que pode ser compilada para IL. Isso também significa que ela precisa ser capaz de interagir com o código escrito em outros idiomas que podem ser usados na plataforma do .NET.

Para fazer isso de forma transparente, deve haver uma maneira comum de descrever todos os tipos com suporte. Isso é o que o CTS (Common Type System) é responsável por fazer. Ele foi feito de várias maneiras:

*   Estabelecer uma estrutura para a execução em qualquer idioma.
*   Fornecer um modelo orientado a objeto para dar suporte à implementação de vários idiomas na plataforma .NET.
*   Definir um conjunto de regras que todas as linguagens devem seguir quando se trata de trabalhar com tipos.
*   Fornecer uma biblioteca que contém os tipos primitivos básicos que são usados no desenvolvimento de aplicativos (ou seja, `Boolean`, `Byte`, `Char` etc.)

O CTS define dois tipos principais que devem ter suporte: tipos de referência e valor. Seus nomes apontam para suas definições.

Os objetos de tipos de referência são representados por uma referência ao valor real do objeto. Uma referência aqui é similar a um ponteiro no C/C++. Ele simplesmente se refere a um local da memória no qual estão os valores dos objetos. Isso tem um profundo impacto sobre como esses tipos são usados. Se você atribuir um tipo de referência a uma variável e, em seguida, passar essa variável em um método, por exemplo, qualquer alteração feita no objeto será refletida no objeto principal. Não há nenhuma cópia.

Tipos de valor são o oposto, no qual os objetos são representados por seus valores. Se você atribuir um tipo de valor a uma variável, você estará, essencialmente, copiando um valor do objeto.

O CTS define várias categorias de tipos, cada um com sua semântica específica e o uso:

*   Classes
*   Estruturas
*   Enums
*   Interfaces
*   Delegados

O CTS também define todas as outras propriedades de tipos, como modificadores de acesso, o que são membros de tipo válidos, como a herança e a sobrecarga funcionam e assim por diante. Infelizmente, se aprofundar em qualquer um deles está além do escopo de um artigo introdutório como este, mas você pode consultar a seção [Mais recursos](#more-resources) no final para obter links para mais conteúdos detalhados que abordam esses tópicos.

## <a name="common-language-specification"></a>Common Language Specification

Para habilitar cenários de interoperabilidade completa, todos os objetos que são criados em código devem se basear em alguns pontos em comum nos idiomas que estão consumindo eles (são seus _chamadores_). Como há vários idiomas diferentes, a plataforma .NET especificou essas semelhanças em algo chamado de CLS **(Common Language Specification)**. A CLS define um conjunto de recursos que são necessários para muitos aplicativos comuns. Ela também fornece uma espécie de receita para qualquer idioma que é implementado na plataforma .NET no que precisar dar suporte.

A CLS é um subconjunto do CTS. Isso significa que todas as regras no CTS também se aplicam à CLS, a menos que as regras da CLS sejam mais estritas. Se um componente é criado usando apenas as regras na CLS, ou seja, ele expõe apenas os recursos da CLS em sua API, ele é chamado de **compatível com CLS**. Por exemplo, os `<framework-librares>` são compatíveis com CLS precisamente porque precisam funcionar em todos os idiomas com suporte na plataforma .NET.

Você pode consultar os documentos na seção [Mais recursos](#more-resources) abaixo para obter uma visão geral de todos os recursos na CLS.

## <a name="more-resources"></a>Mais recursos

*   [Common Type System](https://msdn.microsoft.com/library/zcx1eb1e.aspx)
*   [Common Language Specification](https://msdn.microsoft.com/library/12a7a7h3.aspx)



<!--HONumber=Nov16_HO3-->


