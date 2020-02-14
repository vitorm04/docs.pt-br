---
title: Método XmlReader. CreateSqlReader (System. xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215456"
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
> O método `XmlReader.CreateSqlReader` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Xml>

**Assembly:** System. xml. dll

**.NET Framework versões:** Disponível desde 2,0.
