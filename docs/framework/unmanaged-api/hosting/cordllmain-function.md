---
title: Função _CorDllMain
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616598"
---
# <a name="_cordllmain-function"></a>\_Função CorDllMain

Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hInst`  
 no O identificador de instância do módulo carregado.  
  
 `dwReason`  
 no Indica por que a função de ponto de entrada de DLL está sendo chamada. Esse parâmetro pode ser um dos seguintes valores: DLL \_ PROCESS_ATTACH, dll de \_ thread \_ Attach, dll \_ \_ de anexação de thread \_ ou \_ reanexação de processo de dll. Para obter descrições desses valores, consulte a `DllMain` documentação no Platform SDK.  
  
 `lpReserved`  
 no Não utilizado.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna `true` para êxito e `false` se ocorre um erro.  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada pelo carregador do sistema operacional para assemblies DLL. Para assemblies executáveis, o carregador chama a função [ \_ CorExeMain](corexemain-function.md) em vez disso.  
  
 O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo DLL.  
  
A `_CorDllMain` função é chamada diretamente pelo carregador do sistema operacional.
  
 Para obter informações adicionais, consulte a seção comentários no tópico [ \_ CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Funções estáticas globais de metadados](../metadata/metadata-global-static-functions.md)
