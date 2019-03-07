---
title: Função EnumerateCLRs
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469320"
---
# <a name="enumerateclrs-function"></a>Função EnumerateCLRs
Fornece um mecanismo para enumerar os CLRs em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `debuggeePID`  
 [in] Identificador de processo do processo do qual serão enumeradas CLRs carregados.  
  
 `ppHandleArrayOut`  
 [out] Ponteiro para uma matriz que contém os identificadores de eventos que são usados para continuar a inicialização do CLR. Cada alça na matriz não é garantida para ser válido. Se é válido, o identificador é a ser usado como o evento de inicialização de continuar para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregado no processo.  
  
 `pdwArrayLengthOut`  
 [out] Ponteiro para um DWORD que contém o comprimento de tamanhos iguais `ppHandleArrayOut` e `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_INVALIDARG  
 Tanto `ppHandleArrayOut` ou `ppStringArrayOut` for nulo, ou `pdwArrayLengthOut` é nulo.  
  
 E_OUTOFMEMORY  
 A função não é possível alocar memória suficiente para as matrizes de identificador e o caminho.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Não é possível enumerar CLRs carregados.  
  
## <a name="remarks"></a>Comentários  
 Para um processo de destino que é identificado por `debuggeePID`, a função retorna uma matriz de caminhos `ppStringArrayOut`, para CLRs carregados no processo; uma matriz de identificadores de eventos, `ppHandleArrayOut`, que pode conter um evento de inicialização de continuar para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregados.  
  
 No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.  
  
 A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocados por essa função. Para liberar a memória alocada, você deve chamar [função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Essa função pode ser chamada com ambos os parâmetros de matriz definidos como nulo para não retornar a contagem de CLRs no processo de destino. Essa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim  
  
 **Versões do .NET framework:** 3,5 SP1
