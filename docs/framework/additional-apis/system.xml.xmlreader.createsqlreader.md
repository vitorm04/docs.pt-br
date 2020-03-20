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
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="c41b7-102">Método XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="c41b7-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="c41b7-103">Cria uma nova instância <xref:System.Xml.XmlReader> usando as informações de fluxo, configurações e contexto especificadas para análise.</span><span class="sxs-lookup"><span data-stu-id="c41b7-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="c41b7-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c41b7-104">Parameters</span></span>

- <span data-ttu-id="c41b7-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="c41b7-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="c41b7-106">O fluxo que contém os dados XML.</span><span class="sxs-lookup"><span data-stu-id="c41b7-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="c41b7-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="c41b7-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="c41b7-108">As configurações para a nova instância <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c41b7-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="c41b7-109">Esse valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="c41b7-109">This value can be `null`.</span></span>

- <span data-ttu-id="c41b7-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="c41b7-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="c41b7-111">As informações de contexto necessárias para analisar o fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="c41b7-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="c41b7-112">Esse valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="c41b7-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="c41b7-113">Retornos</span><span class="sxs-lookup"><span data-stu-id="c41b7-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="c41b7-114">Um objeto usado para ler os dados XML no fluxo.</span><span class="sxs-lookup"><span data-stu-id="c41b7-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="c41b7-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c41b7-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c41b7-116">O `XmlReader.CreateSqlReader` método é interno e não deve ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="c41b7-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c41b7-117">A Microsoft não suporta o uso deste método em um aplicativo de produção nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="c41b7-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c41b7-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c41b7-118">Requirements</span></span>

<span data-ttu-id="c41b7-119">**Espaço de nome:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="c41b7-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="c41b7-120">**Montagem:** System.xml.dll</span><span class="sxs-lookup"><span data-stu-id="c41b7-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="c41b7-121">**Versões do Framework .NET:** Disponível desde 2.0.</span><span class="sxs-lookup"><span data-stu-id="c41b7-121">**.NET Framework versions:** Available since 2.0.</span></span>
