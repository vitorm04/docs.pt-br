---
title: "Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0c4192c94d70bd9406607d645716e4dd6f8b957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo
Recupera um mapa de dicionário genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppMemoryBuffer`  
 [out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém o mapa de dicionário genérico. Consulte a seção Comentários para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
 O mapa consiste em duas seções de nível superior:  
  
-   Um [diretório](#Directory) que contém os endereços virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.  
  
-   Um byte alinhado [heap](#Heap) que contém informações de instanciação do objeto. Ele inicia imediatamente após a última entrada de diretório.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>O diretório  
 Cada entrada no diretório refere-se a um deslocamento dentro de heap; ou seja, é um deslocamento relativo ao início da pilha. O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontar para o mesmo deslocamento no heap.  
  
 A parte do diretório do mapa do dicionário genérico tem a seguinte estrutura:  
  
-   Os primeiros 4 bytes contém o número de entradas de dicionário (ou seja, o número de endereços virtuais relativos no dicionário). Chamaremos esse valor como *N*. Se o bit alto for definido, as entradas são classificadas por endereço virtual relativo em ordem crescente.  
  
-   O *N* execute as entradas de diretório. Cada entrada consiste em 8 bytes, de dois segmentos de 4 bytes:  
  
    -   Bytes de 0 a 3: RVA; endereço virtual relativo do dicionário.  
  
    -   Bytes de 4 a 7: deslocamento; um deslocamento em relação ao início da pilha.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>O Heap  
 Tamanho do heap pode ser calculado por um leitor de fluxo subtraindo-se o comprimento do fluxo de tamanho de diretório + 4. Em outras palavras:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 onde é o tamanho da pasta `N * 8`.  
  
 O formato para cada item de informação de instanciação no heap é:  
  
-   O comprimento deste item de informações de instanciação em bytes, no formato compactado de metadados ECMA. O valor exclui essas informações de comprimento.  
  
-   O número de tipos de instanciação genérica ou *T*, em formato compactado de metadados ECMA.  
  
-   *T* tipos, cada um representado no formato de assinatura de tipo ECMA.  
  
 A inclusão do comprimento de cada elemento de heap ativa a classificação simples da seção de diretório sem afetar o heap.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugSymbolProvider2](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
