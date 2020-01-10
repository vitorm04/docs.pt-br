---
title: Serializar e desserializar JSON C# usando-.net
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6561d5e1580e1170369622ebc7bb330ff4e0964f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705776"
---
# <a name="json-serialization-in-net---overview"></a>Serialização JSON no .NET-visão geral

O namespace `System.Text.Json` fornece funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).

O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos. O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.

A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória. Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres. 

## <a name="how-to-get-the-library"></a>Como obter a biblioteca

* A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .
* Para outras estruturas de destino, instale o pacote NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . O pacote dá suporte a:
  * .NET Standard 2,0 e versões posteriores
  * .NET Framework 4.6.1 e versões posteriores
  * .NET Core 2,0, 2,1 e 2,2

## <a name="additional-resources"></a>Recursos adicionais

* [Como usar a biblioteca](system-text-json-how-to.md)
* [Código-fonte](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [Referência de API](xref:System.Text.Json)
* [Roadmap](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* Problemas do GitHub no repositório dotnet/corefx
  * [Discussão sobre o desenvolvimento de System. Text. JSON](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [Todos os problemas de System. Text. JSON](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problemas de System. Text. JSON rotulados como JSON-funcionalidade-doc](https://github.com/dotnet/runtime/labels/json-functionality-doc)
