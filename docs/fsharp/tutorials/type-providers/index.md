---
title: Provedores de tipos
description: Provedores de tipos
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
translationtype: Human Translation
ms.sourcegitcommit: 0a01ec92a90d99fafaacbd3f71f5177e5cf94a68
ms.openlocfilehash: e9e67e6531e0c1daad0c0d4a9f778670d5cb2263
ms.lasthandoff: 04/05/2017

---

# <a name="type-providers"></a>Provedores de tipos

> [!NOTE]
Este guia foi escrito para F# 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

Um provedor de tipos F# é um componente que fornece tipos, propriedades e métodos para uso em seu programa. Provedores de tipos são uma parte significativa do suporte de F# 3.0 para programação rica de informações. A chave para programação rica em informações é eliminar barreiras para trabalhar com várias fontes de informação encontradas na Internet e em ambientes empresariais modernos. Uma barreira significativa para incluir uma fonte de informação em um programa é a necessidade de representar essas informações como tipos, propriedades e métodos para uso em um ambiente da linguagem de programação. Escrever esses tipos manualmente é muito demorado e difícil de manter. Uma alternativa comum é usar um gerador de código que adicione arquivos para seu projeto; no entanto, os tipos convencionais de geração de código não se integram bem nos modos exploratórios de programação com suporte em F# porque o código gerado deve ser substituído sempre que uma referência de serviço é definida.

Os tipos fornecidos pelos provedores de tipo F# geralmente são baseados em fontes de informações externas. Por exemplo, um provedor de tipos F# para SQL fornecerá os tipos, as propriedades e os métodos necessários para trabalhar diretamente com as tabelas de qualquer banco de dados SQL ao qual você tenha acesso. Da mesma forma, um provedor de tipos para serviços Web WSDL fornecerá os tipos, as propriedades e os métodos necessários para trabalhar diretamente com qualquer serviço Web WSDL.

O conjunto de tipos, propriedades e métodos fornecidos por um provedor de tipos F# pode depender de parâmetros fornecidos no código de programa. Por exemplo, um provedor de tipos pode fornecer tipos diferentes dependendo de uma cadeia de conexão ou de uma URL de serviço. Dessa forma, o espaço de informações disponível por meio de uma cadeia de conexão ou URL é integrado diretamente em seu programa. Um provedor de tipos também pode garantir que os grupos de tipos sejam expandidos sob demanda; isto é, eles serão expandidos se os tipos forem realmente referenciados pelo seu programa. Isso permite a integração direta e sob demanda de espaços de informações em grande escala como mercados de dados online de uma forma fortemente tipada.

O F# contém vários provedores de tipos internos para serviços de dados corporativos e da Internet comumente usados. Esses provedores de tipos fornecem acesso simples e normal a bancos de dados SQL relacionais e a serviços OData e WSDL baseados em rede e oferecem suporte auso de consultas F# LINQ com base nessas fontes de dados.

Onde necessário, você poderá criar seus próprios provedores de tipos personalizados ou referenciar provedores de tipos que foram criados por outros. Por exemplo, suponha que sua organização tenha um serviço de dados que forneça um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis. Você pode optar por criar um provedor de tipos que leia os esquemas e apresente os conjuntos de dados mais recentes disponíveis para o programador de uma forma fortemente tipada.


## <a name="related-topics"></a>Tópicos relacionados


|Título|Descrição|
|-----|-----------|
|[Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos](accessing-a-sql-database.md)|Explica como usar o provedor de tipos SqlDataConnection para acessar as tabelas e os procedimentos armazenados de um banco de dados SQL com base em uma cadeia de conexão para uma conexão direta a um banco de dados. O acesso usa um mapeamento LINQ to SQL.|
|[Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades](accessing-a-sql-database-entities.md)|Explica como usar o provedor de tipos SqlEntityConnection para acessar as tabelas e os procedimentos armazenados de um banco de dados SQL com base em uma cadeia de conexão para uma conexão direta a um banco de dados. O acesso usa um mapeamento LINQ to Entities. Este método funciona com qualquer banco de dados, mas o exemplo é demonstrado com o SQL Server.|
|[Instruções passo a passo: acessando um serviço OData por meio de provedores de tipos](accessing-an-odata-service.md)|Explica como usar o provedor de tipos ODataService para acessar um serviço OData de uma forma fortemente tipada com base em uma URL de serviço.|
|[Instruções passo a passo: acessando um serviço Web por meio de provedores de tipos](accessing-a-web-service.md)|Explica como usar o provedor de tipos WsdlService para acessar um serviço Web WSDL de uma forma fortemente tipada com base em uma URL de serviço.|
|[Instruções passo a passo: gerando tipos F&#35; com base em um arquivo DBML](generating-fsharp-types-from-dbml.md)|Explica como usar o provedor de tipos DbmlFile para acessar as tabelas e os procedimentos armazenados de um banco de dados SQL, com base em um arquivo DBML que fornece uma especificação de esquema de banco de dados Linq to SQL.|
|[Instruções passo a passo: gerando tipos F&#35; com base em um arquivo de esquema EDMX](generating-fsharp-types-from-edmx.md)|Explica como usar o provedor de tipos EdmxFile para acessar as tabelas e os procedimentos armazenados de um banco de dados SQL com base em um arquivo EDMX que fornece uma especificação de esquema Entity Framework.|
|[Tutorial: Criar um provedor de tipos ](creating-a-type-provider.md)|Fornece informações sobre como escrever seus próprios provedores de tipos personalizados.|
|[Segurança do provedor de Tipos](type-provider-security.md)|Fornece informações sobre considerações de segurança ao se desenvolver provedores de tipos.|
|[Solução de problemas de Provedores de Tipos](troubleshooting-type-providers.md)|Fornece informações sobre problemas comuns que podem ocorrer ao trabalhar com provedores de tipos e incluem sugestões para soluções.|

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](../../language-reference/index.md)

[Visual F#](../../index.md)
