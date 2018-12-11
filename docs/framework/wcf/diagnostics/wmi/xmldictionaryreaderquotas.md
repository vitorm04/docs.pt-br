---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153131"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="2e543-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2e543-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="2e543-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2e543-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e543-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e543-104">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2e543-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2e543-105">Methods</span></span>  
 <span data-ttu-id="2e543-106">A classe XmlDictionaryReaderQuotas não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="2e543-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e543-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2e543-107">Properties</span></span>  
 <span data-ttu-id="2e543-108">A classe XmlDictionaryReaderQuotas tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2e543-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="2e543-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="2e543-109">MaxArrayLength</span></span>  
 <span data-ttu-id="2e543-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2e543-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e543-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e543-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e543-112">A extensão máxima permitida da matriz.</span><span class="sxs-lookup"><span data-stu-id="2e543-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="2e543-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="2e543-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="2e543-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2e543-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e543-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e543-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e543-116">O máximo de bytes permitidos retornados para cada leitura.</span><span class="sxs-lookup"><span data-stu-id="2e543-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="2e543-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="2e543-117">MaxDepth</span></span>  
 <span data-ttu-id="2e543-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2e543-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e543-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e543-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e543-120">A profundidade máxima do nó aninhado para cada leitura.</span><span class="sxs-lookup"><span data-stu-id="2e543-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="2e543-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="2e543-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="2e543-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2e543-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e543-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e543-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e543-124">O máximo de caracteres permitidos no nome da tabela.</span><span class="sxs-lookup"><span data-stu-id="2e543-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="2e543-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="2e543-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="2e543-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2e543-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e543-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e543-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e543-128">O máximo de caracteres permitidos no conteúdo do elemento XML.</span><span class="sxs-lookup"><span data-stu-id="2e543-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e543-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e543-129">Requirements</span></span>  
  
|<span data-ttu-id="2e543-130">MOF</span><span class="sxs-lookup"><span data-stu-id="2e543-130">MOF</span></span>|<span data-ttu-id="2e543-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2e543-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e543-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="2e543-132">Namespace</span></span>|<span data-ttu-id="2e543-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2e543-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e543-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e543-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
