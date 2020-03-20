---
title: Método XmlReader.CreateSqlReader (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155733"
---
# <a name="xmlreadercreatesqlreader-method"></a>Método XmlReader.CreateSqlReader

Cria uma nova instância <xref:System.Xml.XmlReader> usando as informações de fluxo, configurações e contexto especificadas para análise.

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>parâmetros

- `input` <xref:System.IO.Stream>  
  O fluxo que contém os dados XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  As configurações para a nova instância <xref:System.Xml.XmlReader>. Esse valor pode ser `null`.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  As informações de contexto necessárias para analisar o fragmento XML. Esse valor pode ser `null`.

## <a name="returns"></a>Retornos

<xref:System.Xml.XmlReader>  
Um objeto usado para ler os dados XML no fluxo.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `XmlReader.CreateSqlReader` método é interno e não deve ser usado diretamente em seu código.
>
> A Microsoft não suporta o uso deste método em um aplicativo de produção nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Espaço de nome:**<xref:System.Xml>

**Montagem:** System.xml.dll

**Versões do Framework .NET:** Disponível desde 2.0.
