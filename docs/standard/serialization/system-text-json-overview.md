---
title: Serializar e desserializar JSON usando C#-.NET
description: Esta visão geral descreve a System.Text.Json funcionalidade de namespace para serialização e desserialização do JSON no .net.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d8bd5bcf78db534bd722972db01253cbd13a7a06
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282408"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>Serialização e desserialização JSON (empacotamento e desempacotamento) no .NET-visão geral

O `System.Text.Json` namespace fornece a funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).

O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos. O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.

A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória. Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres.

## <a name="how-to-get-the-library"></a>Como obter a biblioteca

* A biblioteca é interna como parte da estrutura compartilhada para .NET Core 3,0 e versões posteriores.
* Para versões anteriores do Framework, instale o [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) pacote NuGet. O pacote dá suporte a:

  * .NET Standard 2,0 e versões posteriores
  * .NET Framework 4.7.2 e versões posteriores
  * .NET Core 2,0, 2,1 e 2,2

## <a name="additional-resources"></a>Recursos adicionais

* [Como usar a biblioteca](system-text-json-how-to.md)
* [Como migrar do Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Como escrever conversores](system-text-json-converters-how-to.md)
* [System.Text.Json código-fonte](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [System.Text.Json Referência de API](xref:System.Text.Json)
* [System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
