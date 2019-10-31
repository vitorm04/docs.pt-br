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
ms.openlocfilehash: 272856c7eedbdc577158edcc463535a7946bb060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122984"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_a função StackTrace
Fornece uma representação de texto de um rastreamento de pilha gerenciado e uma matriz de registros de `CONTEXT`, um para cada transição entre código gerenciado e não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no O cliente que está sendo depurado.  
  
 `wszTextOut`  
 fora A representação de texto do rastreamento de pilha.  
  
 `puiTextLength`  
 fora Um ponteiro para o número de caracteres em `wszTextOut`.  
  
 `pTransitionContexts`  
 fora A matriz de contextos de transição.  
  
 `puiTransitionContextCount`  
 fora Um ponteiro para o número de contextos de transição na matriz.  
  
 `uiSizeOfContext`  
 no O tamanho da estrutura de contexto.  
  
 `Flags`  
 no Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro de EBP e o ponteiro de pilha Enter (ESP) na frente de cada linha de `module!functionname`.  
  
## <a name="remarks"></a>Comentários  
 A estrutura de `_EFN_StackTrace` pode ser chamada de uma interface programática do WinDbg. Os parâmetros são usados da seguinte maneira:  
  
- Se `wszTextOut` for NULL e `puiTextLength` não for NULL, a função retornará o comprimento da cadeia de caracteres em `puiTextLength`.  
  
- Se `wszTextOut` não for NULL, a função armazenará texto em `wszTextOut` até o local indicado por `puiTextLength`. Ele retorna com êxito se havia espaço suficiente no buffer ou retorna E_OUTOFMEMORY se o buffer não era longo o suficiente.  
  
- A parte de transição da função será ignorada se `pTransitionContexts` e `puiTransitionContextCount` forem nulos. Nesse caso, a função fornece chamadores com a saída de texto apenas dos nomes de função.  
  
- Se `pTransitionContexts` for NULL e `puiTransitionContextCount` não for NULL, a função retornará o número necessário de entradas de contexto em `puiTransitionContextCount`.  
  
- Se `pTransitionContexts` não for NULL, a função o tratará como uma matriz de estruturas de comprimento `puiTransitionContextCount`. O tamanho da estrutura é fornecido por `uiSizeOfContext`e deve ser o tamanho de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.  
  
- `wszTextOut` é gravado no seguinte formato:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Se o deslocamento em Hex for 0x0, nenhum deslocamento será gravado.  
  
- Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará SOS_E_NOMANAGEDCODE.  
  
- O parâmetro `Flags` é 0 ou SOS_STACKTRACE_SHOWADDRESSES para ver EBP e ESP na frente de cada linha de `module!functionname`. Por padrão, é 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** SOS_Stacktrace. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
