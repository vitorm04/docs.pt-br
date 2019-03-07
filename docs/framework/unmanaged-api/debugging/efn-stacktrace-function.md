---
title: Função _EFN_StackTrace
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3187809fadb275ed54a450f456d98d140d1100c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485881"
---
# <a name="efnstacktrace-function"></a>Função _EFN_StackTrace
Fornece uma representação de texto de um rastreamento de pilha gerenciada e uma matriz de `CONTEXT` registra, um para cada transição entre não gerenciado e código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Client`  
 [in] O cliente que está sendo depurado.  
  
 `wszTextOut`  
 [out] A representação de texto de rastreamento de pilha.  
  
 `puiTextLength`  
 [out] Um ponteiro para o número de caracteres em `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] A matriz de contextos de transição.  
  
 `puiTransitionContextCount`  
 [out] Um ponteiro para o número de contextos de transição na matriz.  
  
 `uiSizeOfContext`  
 [in] O tamanho da estrutura de contexto.  
  
 `Flags`  
 [in] Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro EBP e o ponteiro de pilha de enter (ESP) na frente de cada `module!functionname` linha.  
  
## <a name="remarks"></a>Comentários  
 O `_EFN_StackTrace` estrutura pode ser chamada de uma interface programática do WinDbg. Parâmetros são usados da seguinte maneira:  
  
-   Se `wszTextOut` for null e `puiTextLength` for não nulo, a função retorna o comprimento da cadeia de caracteres em `puiTextLength`.  
  
-   Se `wszTextOut` é diferente de null, a função armazena o texto no `wszTextOut` até o local indicado pelo `puiTextLength`. Retorna com êxito se não havia espaço suficiente no buffer ou retorna E_OUTOFMEMORY se o buffer não era longo o suficiente.  
  
-   A parte da transição da função será ignorada se `pTransitionContexts` e `puiTransitionContextCount` forem ambos nulos. Nesse caso, a função fornece chamadores com saída de texto de somente os nomes de função.  
  
-   Se `pTransitionContexts` for null e `puiTransitionContextCount` for não nulo, a função retorna o número necessário de entradas de contexto no `puiTransitionContextCount`.  
  
-   Se `pTransitionContexts` é diferente de null, a função tratará como uma matriz de estruturas de comprimento `puiTransitionContextCount`. O tamanho da estrutura será determinado pelos `uiSizeOfContext`, e deve ser o tamanho de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.  
  
-   `wszTextOut` é escrito no seguinte formato:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Se o deslocamento em hexadecimal é 0x0, deslocamento não será gravado.  
  
-   Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retorna SOS_E_NOMANAGEDCODE.  
  
-   O `Flags` parâmetro é 0 ou SOS_STACKTRACE_SHOWADDRESSES ver EBP e ESP na frente de cada `module!functionname` linha. Por padrão, é 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** SOS_Stacktrace.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
