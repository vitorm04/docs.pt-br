---
title: Método ISymUnmanagedWriter::OpenMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610035"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="998b0-102">Método ISymUnmanagedWriter::OpenMethod</span><span class="sxs-lookup"><span data-stu-id="998b0-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="998b0-103">Abre um método no qual as informações de símbolo são emitidas.</span><span class="sxs-lookup"><span data-stu-id="998b0-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="998b0-104">O método fornecido torna-se o método atual para chamadas para definir pontos de sequência, parâmetros e escopos léxicos.</span><span class="sxs-lookup"><span data-stu-id="998b0-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="998b0-105">Há um escopo lexical implícito em todo o método.</span><span class="sxs-lookup"><span data-stu-id="998b0-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="998b0-106">Reabrir um método que foi fechado anteriormente apaga todos os símbolos definidos anteriormente para esse método.</span><span class="sxs-lookup"><span data-stu-id="998b0-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="998b0-107">Pode haver apenas um método Open por vez.</span><span class="sxs-lookup"><span data-stu-id="998b0-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="998b0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="998b0-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="998b0-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="998b0-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="998b0-110">no O token de metadados para o método a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="998b0-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="998b0-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="998b0-111">Return Value</span></span>  
 <span data-ttu-id="998b0-112">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="998b0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="998b0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="998b0-113">Requirements</span></span>  
 <span data-ttu-id="998b0-114">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="998b0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998b0-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="998b0-115">See also</span></span>

- [<span data-ttu-id="998b0-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="998b0-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="998b0-117">Método CloseMethod</span><span class="sxs-lookup"><span data-stu-id="998b0-117">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="998b0-118">Método OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="998b0-118">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
