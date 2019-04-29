---
title: Função GetALinkMessageDll
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789890"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="348de-102">Função GetALinkMessageDll</span><span class="sxs-lookup"><span data-stu-id="348de-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="348de-103">Localiza e carrega a DLL da mensagem.</span><span class="sxs-lookup"><span data-stu-id="348de-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="348de-104">Retorna 0 se a DLL da mensagem não pode ser localizado ou carregado.</span><span class="sxs-lookup"><span data-stu-id="348de-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="348de-105">A DLL de mensagem deve ser em um subdiretório, cujo nome é uma ID de idioma ou no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="348de-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348de-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="348de-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="348de-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="348de-107">Requirements</span></span>  
 <span data-ttu-id="348de-108">**Cabeçalho:** alink.h</span><span class="sxs-lookup"><span data-stu-id="348de-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="348de-109">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="348de-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348de-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="348de-110">See also</span></span>

- [<span data-ttu-id="348de-111">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="348de-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
