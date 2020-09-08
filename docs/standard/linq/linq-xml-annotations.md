---
title: Anotações-LINQ to XML
description: Saiba como usar anotações no LINQ to XML para associar qualquer objeto arbitrário de qualquer tipo arbitrário a qualquer componente XML em uma árvore XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551986"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a><span data-ttu-id="ddf88-103">LINQ to XML anotações (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ddf88-103">LINQ to XML annotations (LINQ to XML)</span></span>

<span data-ttu-id="ddf88-104">As anotações no LINQ to XML permitem que você associe qualquer objeto arbitrário de qualquer tipo arbitrário a qualquer componente XML em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="ddf88-104">Annotations in LINQ to XML enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="ddf88-105">Para adicionar uma anotação a um componente XML, como <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você chama o método de <xref:System.Xml.Linq.XObject.AddAnnotation%2A> .</span><span class="sxs-lookup"><span data-stu-id="ddf88-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="ddf88-106">Você recupera anotações pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="ddf88-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="ddf88-107">Observe que as anotações não fazem parte do XML infoset; Eles não são serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="ddf88-107">Note that annotations aren't part of the XML infoset; they're not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="ddf88-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="ddf88-108">Methods</span></span>

<span data-ttu-id="ddf88-109">Você pode usar os seguintes métodos para trabalhar com anotações:</span><span class="sxs-lookup"><span data-stu-id="ddf88-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="ddf88-110">Método</span><span class="sxs-lookup"><span data-stu-id="ddf88-110">Method</span></span>|<span data-ttu-id="ddf88-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddf88-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="ddf88-112">Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ddf88-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="ddf88-113">Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ddf88-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="ddf88-114">Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ddf88-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="ddf88-115">Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ddf88-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
