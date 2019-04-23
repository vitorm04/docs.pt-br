---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978166"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="eaebf-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="eaebf-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="eaebf-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="eaebf-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaebf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eaebf-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eaebf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="eaebf-105">Methods</span></span>  
 <span data-ttu-id="eaebf-106">A classe MtomMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="eaebf-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eaebf-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eaebf-107">Properties</span></span>  
 <span data-ttu-id="eaebf-108">A classe MtomMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="eaebf-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="eaebf-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="eaebf-109">Encoding</span></span>  
 <span data-ttu-id="eaebf-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="eaebf-110">Data type: string</span></span>  
  
 <span data-ttu-id="eaebf-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="eaebf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eaebf-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="eaebf-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="eaebf-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="eaebf-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="eaebf-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="eaebf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="eaebf-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="eaebf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eaebf-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="eaebf-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="eaebf-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="eaebf-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="eaebf-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="eaebf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="eaebf-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="eaebf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eaebf-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="eaebf-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="eaebf-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="eaebf-121">ReaderQuotas</span></span>  
 <span data-ttu-id="eaebf-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="eaebf-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="eaebf-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="eaebf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eaebf-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="eaebf-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaebf-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaebf-125">Requirements</span></span>  
  
|<span data-ttu-id="eaebf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="eaebf-126">MOF</span></span>|<span data-ttu-id="eaebf-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="eaebf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eaebf-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="eaebf-128">Namespace</span></span>|<span data-ttu-id="eaebf-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eaebf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eaebf-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaebf-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
