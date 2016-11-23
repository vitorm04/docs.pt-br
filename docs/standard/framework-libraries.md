---
title: Bibliotecas do Framework
description: Bibliotecas do Framework
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
translationtype: Human Translation
ms.sourcegitcommit: 093b852fe1ed2307ebce914381fe47388b435c95
ms.openlocfilehash: c11f89522a97d60f5ffb8588f4500b64b5d2d6db

---

# <a name="framework-libraries"></a>Bibliotecas do Framework

O .NET tem um conjunto padrão expansivo de bibliotecas de classes, conhecido como as bibliotecas de classes base (conjunto principal) ou as bibliotecas de classes .NET Framework (conjunto completo). Essas bibliotecas fornecem implementações para muitos algoritmos, funcionalidades do utilitário e tipos gerais e específicos do aplicativo. Tanto bibliotecas comerciais quanto comunitárias são criadas com base nas bibliotecas de classes .NET Framework, fornecendo bibliotecas off-the-shelf fáceis de usar para uma amplo conjunto de tarefas de computação.

Um subconjunto dessas bibliotecas é fornecido com cada implementação do .NET. APIs de BCL (bibliotecas de classes base) são esperadas com qualquer implementação do .NET, porque os desenvolvedores desejarão tê-las e porque bibliotecas populares precisarão delas para serem executadas. Bibliotecas específicas de aplicativo acima da BCL, como ASP.NET, não estarão disponíveis em todas as implementações do .NET.

## <a name="base-class-libraries"></a>Bibliotecas de classes base

As BCL fornecem a funcionalidade de utilitário e tipos mais básicos e são a base de todas as outras bibliotecas de classes do .NET. Elas têm o objetivo de fornecer implementações de caráter bastante geral, sem nenhum desvio para nenhuma carga de trabalho. O desempenho é sempre uma consideração importante, já que os aplicativos podem preferir uma política específica como baixa latência para alta taxa de transferência ou memória insuficiente para baixo uso de CPU. Essas bibliotecas estão destinadas a, em termos gerais, serem de alto desempenho e adotarem uma abordagem intermediária acordo com essas preocupações de desempenho diversas. Para a maioria dos aplicativos, essa abordagem tem sido muito bem-sucedida.

## <a name="primitive-types"></a>Tipos primitivos

O .NET inclui um conjunto de tipos primitivos, que são usados (em graus variáveis) em todos os programas. Esses tipos contêm dados, como números, cadeias de caracteres, bytes e objetos arbitrários. A linguagem C# inclui palavras-chave para esses tipos. Um conjunto de amostra desses tipos é listado abaixo, com palavras-chave do C# correspondentes.

*   [System.Object](https://msdn.microsoft.com/library/system.object.aspx) ([object](https://msdn.microsoft.com/library/9kkx3h3c.aspx)) – a classe base ultimate no sistema de tipos CLR. É a raiz da hierarquia de tipos.
*   [System.Int16](https://msdn.microsoft.com/library/system.int16.aspx) ([short](https://msdn.microsoft.com/library/ybs77ex4.aspx)) – tipo inteiro com sinal de 16 bits. O [UInt16](https://msdn.microsoft.com/library/system.uint16.aspx) sem sinal também existe.
*   [System.Int32](https://msdn.microsoft.com/library/system.int32.aspx) ([int](https://msdn.microsoft.com/library/5kzh1b5w.aspx)) – tipo inteiro com sinal de 32 bits. O [UInt32](https://msdn.microsoft.com/library/x0sksh43.aspx) sem sinal também existe.
*   [System.Single](https://msdn.microsoft.com/library/system.single.aspx) ([float](https://msdn.microsoft.com/library/b1e65aza.aspx)) – um tipo de ponto flutuante de 32 bits.
*   [System.Decimal](https://msdn.microsoft.com/library/system.decimal.aspx) ([decimal](https://msdn.microsoft.com/library/364x0z75.aspx)) – um tipo decimal de 128 bits.
*   [System.Byte](https://msdn.microsoft.com/library/system.byte.aspx) ([byte](https://msdn.microsoft.com/library/5bdb6693.aspx)) – um inteiro de 8 bits sem sinal que representa um byte de memória.
*   [System. Boolean](https://msdn.microsoft.com/library/system.boolean.aspx) ([bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx)) – um tipo booliano representando 'true' ou 'false'.
*   [System.Char](https://msdn.microsoft.com/library/system.char.aspx) ([char](https://msdn.microsoft.com/library/x9h8tsay.aspx)) – um tipo numérico de 16 bits que representa um caractere Unicode.
*   [System.String](https://msdn.microsoft.com/library/system.string.aspx) ([string](https://msdn.microsoft.com/library/362314fe.aspx)) – representa uma série de caracteres. Diferente de um `char[]`, mas permite a indexação em cada `char` individual em `string`.

## <a name="data-structures"></a>Estruturas de dados

O .NET inclui um conjunto de estruturas de dados que são burros de carga de quase todos os aplicativos .NET. Elas são em sua maioria coleções, mas também incluem outros tipos.

*   [Matriz](https://msdn.microsoft.com/library/system.array.aspx) – representa uma matriz de objetos fortemente tipados que podem ser acessados por índice. Tem um tamanho fixo, de acordo com sua construção.
*   [Lista](https://msdn.microsoft.com/library/6sh2ey19.aspx) – representa uma lista fortemente tipada de objetos que podem ser acessados por índice. É redimensionado automaticamente conforme necessário.
*   [Dicionário](https://msdn.microsoft.com/library/xfhwa508.aspx) – representa uma coleção de valores que são indexados por uma chave. Os valores podem ser acessados via chave. É redimensionado automaticamente conforme necessário.
*   [Uri](https://msdn.microsoft.com/library/system.uri.aspx) – fornece uma representação de objeto de um URI (Uniform Resource Identifier) e fácil acesso às partes do URI.
*   [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx) – representa um momento no tempo, geralmente expresso como uma data e hora do dia.

## <a name="utility-apis"></a>APIs utilitárias

O .NET inclui um conjunto de APIs utilitárias que fornecem funcionalidade para várias tarefas importantes.

*   [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient.aspx) – uma API para enviar solicitações HTTP e receber respostas HTTP de um recurso identificado por um URI.
*   [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx) – Uma API para carregar e consultar documentos XML com o LINQ.
*   [StreamReader](https://msdn.microsoft.com/library/system.io.streamreader.aspx) – Uma API para ler arquivos ([StreamWriter](https://msdn.microsoft.com/library/system.io.stringwriter.aspx) pode ser usado para gravar arquivos).

## <a name="app-model-apis"></a>APIs do modelo de aplicativo

Há muitos modelos de aplicativo que podem ser usados com o .NET, fornecidos por várias empresas.

*   [ASP.NET](http://asp.net) – fornece uma estrutura da Web para a criação de sites e serviços. Suporte para Windows, Linux e macOS (depende de versão do ASP.NET).



<!--HONumber=Nov16_HO4-->


