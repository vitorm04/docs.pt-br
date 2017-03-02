---
title: "Compilação e reutilização em expressões regulares"
description: "Compilação e reutilização em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3adea434-e2ed-4023-b4f5-b0608b4cf53f
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 7b3acb4571cddc19520f8534828d94844c9d59e6
ms.lasthandoff: 03/02/2017

---

# <a name="compilation-and-reuse-in-regular-expressions"></a>Compilação e reutilização em expressões regulares

Você pode otimizar o desempenho de aplicativos que fazem uso intensivo de expressões regulares compreendendo como o mecanismo de expressões regulares compila expressões e como as expressões regulares são armazenadas em cache. Este tópico discute a compilação e o cache.

## <a name="compiled-regular-expressions"></a>Expressões regulares compiladas

Por padrão, o mecanismo de expressões regulares compila uma expressão regular para uma sequência de instruções internas (esses são códigos de alto nível que são diferentes da Microsoft Intermediate Language ou MSIL). Quando o mecanismo executa uma expressão regular, ele interpreta os códigos internos.

Se um objeto [Regex](xref:System.Text.RegularExpressions.Regex) for construído com a opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled), ele compila a expressão regular para o código explícito em MSIL, em vez de instruções internas de expressões regulares de alto nível. Isso permite que o compilador JIT (just-in-time) do .NET converta a expressão para um código de computador nativo para um melhor desempenho.

No entanto, a MSIL gerada não pode ser descarregada. A única maneira de descarregar o código é descarregar todo o domínio de aplicativo (ou seja, descarregar todo o código do aplicativo). Na verdade, quando uma expressão regular é compilada com a opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled), o .NET nunca libera os recursos usados pela expressão compilada, mesmo que a expressão regular tenha sido criada por um objeto [Regex](xref:System.Text.RegularExpressions.Regex) liberado para a coleta de lixo.

Você precisa ser cuidadoso para limitar o número de expressões regulares diferentes que compila com a opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) para evitar consumir recursos demais. Se um aplicativo precisar usar um número grande ou ilimitado de expressões regulares, cada expressão deve ser interpretada, não compilada. No entanto, se um número pequeno de expressões regulares forem usadas repetidamente, elas devem ser compiladas com [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) para melhorar o desempenho. 

## <a name="the-regular-expressions-cache"></a>Cache de expressões regulares

Para melhorar o desempenho, o mecanismo de expressões regulares mantém um cache em todo o aplicativo com as expressões regulares compiladas. O cache armazena padrões de expressões regulares que são usados somente em chamadas de método estático. (Padrões de expressão regular fornecidos para métodos de instância não são armazenados). Isso evita a necessidade de analisar novamente uma expressão em código de bytes de alto nível cada vez que ela for usada.

O número máximo de expressões regulares em cache é determinado pelo valor da propriedade `static` (`Shared` no Visual Basic) [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize). Por padrão, o mecanismo de expressões regulares armazena em cache até 15 expressões regulares compiladas. Se o número de expressões regulares compiladas ultrapassar o tamanho do cache, a expressão regular menos utilizada recentemente será descartada e a nova expressão regular será armazenada em cache. 

Seu aplicativo pode tirar proveito de expressões regulares pré-compiladas de uma das duas maneiras a seguir:

* Usando um método estático do objeto [Regex](xref:System.Text.RegularExpressions.Regex) para definir a expressão regular. Se você estiver usando um padrão de expressão regular que já foi definido em outra chamada de método estático, o mecanismo de expressões regulares o recuperará do cache. Caso contrário, o mecanismo compilará a expressão regular e a adicionará ao cache.

* Reutilizando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) enquanto o padrão de expressão regular for necessário.


Devido à sobrecarga da instanciação de objetos e à compilação da expressão regular, criar e destruir rapidamente vários objetos [Regex](xref:System.Text.RegularExpressions.Regex) é um processo muito caro. Para aplicativos que usam um grande número de expressões regulares diferentes, você pode otimizar o desempenho usando chamadas para métodos [Regex](xref:System.Text.RegularExpressions.Regex) estáticos e, possivelmente, aumentando o tamanho do cache de expressão regular.

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)


