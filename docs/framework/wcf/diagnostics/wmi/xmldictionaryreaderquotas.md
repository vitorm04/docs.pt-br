---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="673e4-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="673e4-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="673e4-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="673e4-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="673e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="673e4-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="673e4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="673e4-105">Methods</span></span>  
 <span data-ttu-id="673e4-106">A classe XmlDictionaryReaderQuotas não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="673e4-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="673e4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="673e4-107">Properties</span></span>  
 <span data-ttu-id="673e4-108">A classe XmlDictionaryReaderQuotas tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="673e4-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="673e4-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="673e4-109">MaxArrayLength</span></span>  
 <span data-ttu-id="673e4-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="673e4-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="673e4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="673e4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="673e4-112">A extensão máxima permitida da matriz.</span><span class="sxs-lookup"><span data-stu-id="673e4-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="673e4-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="673e4-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="673e4-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="673e4-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="673e4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="673e4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="673e4-116">O máximo de bytes permitidos retornados para cada leitura.</span><span class="sxs-lookup"><span data-stu-id="673e4-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="673e4-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="673e4-117">MaxDepth</span></span>  
 <span data-ttu-id="673e4-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="673e4-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="673e4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="673e4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="673e4-120">A profundidade máxima do nó aninhado para cada leitura.</span><span class="sxs-lookup"><span data-stu-id="673e4-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="673e4-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="673e4-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="673e4-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="673e4-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="673e4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="673e4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="673e4-124">O máximo de caracteres permitidos no nome da tabela.</span><span class="sxs-lookup"><span data-stu-id="673e4-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="673e4-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="673e4-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="673e4-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="673e4-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="673e4-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="673e4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="673e4-128">O máximo de caracteres permitidos no conteúdo do elemento XML.</span><span class="sxs-lookup"><span data-stu-id="673e4-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="673e4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="673e4-129">Requirements</span></span>  
  
|<span data-ttu-id="673e4-130">MOF</span><span class="sxs-lookup"><span data-stu-id="673e4-130">MOF</span></span>|<span data-ttu-id="673e4-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="673e4-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="673e4-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="673e4-132">Namespace</span></span>|<span data-ttu-id="673e4-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="673e4-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="673e4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="673e4-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
