---
title: "Função EnumerateCLRs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a>Função EnumerateCLRs
Fornece um mecanismo para enumerar CLRs em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `debuggeePID`  
 [in] Identificador de processo do processo do qual serão enumeradas CLRs carregados.  
  
 `ppHandleArrayOut`  
 [out] Ponteiro para uma matriz que contém os identificadores de eventos que são usados para continuar a inicialização do CLR. Não há garantia de que cada alça na matriz de ser válido. Se é válido, o identificador é a ser usado como o evento de inicialização de continuar para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregado no processo.  
  
 `pdwArrayLengthOut`  
 [out] Ponteiro para uma DWORD que contém o comprimento de tamanho igual `ppHandleArrayOut` e `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.  
  
 E_INVALIDARG  
 O `ppHandleArrayOut` ou `ppStringArrayOut` é nulo, ou `pdwArrayLengthOut` é nulo.  
  
 E_OUTOFMEMORY  
 A função é não é possível alocar memória suficiente para as matrizes de identificador e o caminho.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Não é possível enumerar CLRs carregados.  
  
## <a name="remarks"></a>Comentários  
 Para um processo de destino que é identificado pelo `debuggeePID`, a função retorna uma matriz de caminhos, `ppStringArrayOut`, CLRs carregados no processo; uma matriz de identificadores de evento, `ppHandleArrayOut`, que pode conter um evento de inicialização de continuar para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregados.  
  
 No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.  
  
 A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocados por essa função. Para liberar a memória alocada, você deve chamar [função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Esta função pode ser chamada com ambos os parâmetros de matriz definidos como null para retornar a contagem de CLRs no processo de destino. Essa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET framework:** 3.5 SP1
