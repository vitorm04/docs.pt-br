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
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="87131-102">Método XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="87131-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="87131-103">Cria uma nova instância <xref:System.Xml.XmlReader> usando as informações de fluxo, configurações e contexto especificadas para análise.</span><span class="sxs-lookup"><span data-stu-id="87131-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="87131-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="87131-104">Parameters</span></span>

- <span data-ttu-id="87131-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="87131-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="87131-106">O fluxo que contém os dados XML.</span><span class="sxs-lookup"><span data-stu-id="87131-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="87131-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="87131-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="87131-108">As configurações para a nova instância <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="87131-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="87131-109">Esse valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="87131-109">This value can be `null`.</span></span>

- <span data-ttu-id="87131-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="87131-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="87131-111">As informações de contexto necessárias para analisar o fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="87131-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="87131-112">Esse valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="87131-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="87131-113">Retornos</span><span class="sxs-lookup"><span data-stu-id="87131-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="87131-114">Um objeto usado para ler os dados XML no fluxo.</span><span class="sxs-lookup"><span data-stu-id="87131-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="87131-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="87131-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="87131-116">O método `XmlReader.CreateSqlReader` é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="87131-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="87131-117">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="87131-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="87131-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87131-118">Requirements</span></span>

<span data-ttu-id="87131-119">**Namespace:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="87131-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="87131-120">**Assembly:** System. xml. dll</span><span class="sxs-lookup"><span data-stu-id="87131-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="87131-121">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="87131-121">**.NET Framework versions:** Available since 2.0.</span></span>
