---
title: Função CreateHistoryReader
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 80979f0424469bb1d4771ad6507bb8c9d5364ab4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108602"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="8b364-102">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="8b364-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="8b364-103">Cria um leitor de histórico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="8b364-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b364-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b364-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b364-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b364-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="8b364-106">no O caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8b364-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="8b364-107">fora Após a conclusão bem-sucedida, contém um ponteiro para o leitor de histórico.</span><span class="sxs-lookup"><span data-stu-id="8b364-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b364-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8b364-108">Return Value</span></span>  
 <span data-ttu-id="8b364-109">Esse método retorna códigos de erro COM padrão, conforme definido no WinError. h, além dos valores descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b364-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="8b364-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="8b364-110">Return code</span></span>|<span data-ttu-id="8b364-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b364-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8b364-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b364-112">S_OK</span></span>|<span data-ttu-id="8b364-113">Indica que o método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="8b364-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="8b364-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8b364-114">E_INVALIDARG</span></span>|<span data-ttu-id="8b364-115">Indica que `wzFilePath` ou `ppHistoryReader` estão definidas como uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="8b364-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b364-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b364-116">Requirements</span></span>  
 <span data-ttu-id="8b364-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b364-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b364-118">**Biblioteca:** Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="8b364-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="8b364-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b364-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b364-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b364-120">See also</span></span>

- [<span data-ttu-id="8b364-121">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="8b364-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
