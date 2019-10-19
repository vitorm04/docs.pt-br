---
title: Método XmlReader. CreateSqlReader (System. xml)
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584130"
---
# <a name="xmlreadercreatesqlreader-method"></a>Método XmlReader. CreateSqlReader

Cria uma nova instância <xref:System.Xml.XmlReader> usando as informações de fluxo, configurações e contexto especificadas para análise.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parâmetros

- `input` <xref:System.IO.Stream>  
  O fluxo que contém os dados XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  As configurações para a nova instância <xref:System.Xml.XmlReader>. Este valor pode ser `null`.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  As informações de contexto necessárias para analisar o fragmento XML. Este valor pode ser `null`.

## <a name="returns"></a>Retorna

<xref:System.Xml.XmlReader>  
Um objeto usado para ler os dados XML no fluxo.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `XmlReader.CreateSqlReader` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Xml>

**Assembly:** System. xml. dll

**.NET Framework versões:** Disponível desde 2,0.
