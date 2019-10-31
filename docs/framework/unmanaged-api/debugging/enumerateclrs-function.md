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
ms.openlocfilehash: 69288e995ec789091bf089368cd9a60f003df86e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122983"
---
# <a name="enumerateclrs-function"></a>Função EnumerateCLRs
Fornece um mecanismo para enumerar o CLRs em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `debuggeePID`  
 no Identificador do processo do qual o CLRs carregado será enumerado.  
  
 `ppHandleArrayOut`  
 fora Ponteiro para uma matriz que contém identificadores de eventos que são usados para continuar uma inicialização do CLR. Não há garantia de que cada identificador na matriz seja válido. Se for válido, o identificador será usado como o evento continue-Startup para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 fora Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregados no processo.  
  
 `pdwArrayLengthOut`  
 fora Ponteiro para um DWORD que contém o comprimento do `ppHandleArrayOut` e `pdwArrayLengthOut`de tamanho uniforme.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 E_INVALIDARG  
 `ppHandleArrayOut` ou `ppStringArrayOut` é nulo ou o `pdwArrayLengthOut` é nulo.  
  
 E_OUTOFMEMORY  
 A função não pode alocar memória suficiente para as matrizes de identificador e caminho.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Não é possível enumerar o CLRs carregado.  
  
## <a name="remarks"></a>Comentários  
 Para um processo de destino que é identificado pelo `debuggeePID`, a função retorna uma matriz de caminhos, `ppStringArrayOut`, para CLRs carregada no processo; uma matriz de identificadores de eventos, `ppHandleArrayOut`, que pode conter um evento continue-Startup para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregadas.  
  
 No sistema operacional Windows, o `debuggeePID` é mapeado para um identificador de processo do sistema operacional.  
  
 A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocadas por essa função. Para liberar a memória alocada, você deve chamar a [função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Essa função pode ser chamada com ambos os parâmetros de matriz definidos como NULL para retornar a contagem de CLRs no processo de destino. A partir dessa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim. h  
  
 **Biblioteca:** dbgshim. dll  
  
 **Versões do .NET Framework:** 3,5 SP1
