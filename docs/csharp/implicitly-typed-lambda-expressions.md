---
title: "Expressões lambda tipadas implicitamente"
description: "Expressões lambda tipadas implicitamente"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c3621f6feb29929d3681b6ed66cc12c5d8018ba1
ms.lasthandoff: 03/13/2017

---

# <a name="implicitly-typed-lambda-expressions"></a>Expressões lambda tipadas implicitamente

Eu não estou usando `var` para declarar esta árvore de expressão. Você não pode usar uma declaração de variável tipada implicitamente para declarar uma expressão lambda.
Isso cria um problema de lógica circular para o compilador. A declaração `var` diz ao compilador para descobrir o tipo da variável de acordo com o tipo da expressão no lado direito do operador de atribuição. Uma expressão lambda não tem um tipo de tempo de compilação, mas pode ser convertida em qualquer tipo de delegado ou expressão correspondente. Quando atribui uma expressão lambda a uma variável de um tipo de delegado ou expressão, você diz ao compilador para tentar converter a expressão lambda em uma expressão ou delegado que corresponda à assinatura da variável "atribuída". O compilador deve tentar fazer o item do lado direito da atribuição corresponder ao tipo do lado esquerdo da atribuição. 

Os dois lados da atribuição não podem estar dizendo ao compilador para examinar o objeto do outro lado do operador de atribuição para ver se meu tipo é correspondente.

Você pode obter mais detalhes sobre por quê a linguagem C# especifica esse comportamento lendo [este artigo](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (download do PDF)



