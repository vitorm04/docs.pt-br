---
title: Serialização JSON no .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083090"
---
# <a name="json-serialization-in-net"></a>Serialização JSON no .NET

O `System.Text.Json` namespace fornece a funcionalidade para serializar de e para o JavaScript Object Notation (JSON).

O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos. O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.

A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória. Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres. 

## <a name="how-to-get-the-library"></a>Como obter a biblioteca

* A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .
* Para outras estruturas de destino, instale o pacote NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . O pacote dá suporte a:
  * .NET Standard 2,0 e versões posteriores
  * .NET Framework 4,61 e versões posteriores
  * .NET Core 2,0 e versões posteriores

## <a name="additional-resources"></a>Recursos adicionais

* [Como usar a biblioteca](system-text-json-how-to.md)
* [Código-fonte](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Referência de API](xref:System.Text.Json)
* [Roadmap](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Problemas do GitHub no repositório dotnet/corefx
  * [Discussão sobre o desenvolvimento de System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Todos os problemas de System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problemas de System. Text. JSON rotulados como JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
