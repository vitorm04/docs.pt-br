---
title: Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65407fca73971546725d9457d25bf1270d2001e2
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662543"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo

Recupera um mapa de dicionário genérico.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Parâmetros

`ppMemoryBuffer`\
[out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém o mapa de dicionário genérico. Consulte a seção Comentários para obter mais informações.

## <a name="remarks"></a>Comentários

> [!NOTE]
> Esse método só está disponível com o .NET Native.

O mapa consiste em duas seções de nível superior:

- Um [directory](#Directory) que contém os endereços de virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.

- Um byte alinhado [heap](#Heap) que contém informações de instanciação do objeto. Ele começa imediatamente após a última entrada de diretório.

<a name="Directory"></a>

## <a name="the-directory"></a>O diretório

Cada entrada no diretório refere-se a um deslocamento dentro de heap; ou seja, é um deslocamento relativo ao início do heap. O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontar para o mesmo deslocamento no heap.

A parte do diretório do mapa do dicionário genérico tem a seguinte estrutura:

- Os primeiros 4 bytes contém o número de entradas de dicionário (ou seja, o número de endereços virtuais no dicionário). Vamos nos referir a esse valor como *N*. Se o bit alto for definido, as entradas são classificadas pelo endereço virtual relativo em ordem crescente.

- O *N* execute as entradas de diretório. Cada entrada consiste em 8 bytes, de dois segmentos de 4 bytes:

  - Bytes de 0 a 3: RVA; endereço virtual relativo do dicionário.

  - Bytes de 4 a 7: Deslocamento; um deslocamento relativo para o início do heap.

<a name="Heap"></a>

## <a name="the-heap"></a>O Heap

Tamanho do heap pode ser calculado por um leitor de fluxo, subtraindo o tamanho do fluxo de tamanho de diretório + 4. Em outras palavras:

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

onde o tamanho do diretório é `N * 8`.

O formato para cada item de informações de instanciação no heap é:

- O comprimento deste item de informações de instanciação em bytes, no formato compactado de metadados ECMA. O valor exclui essas informações de comprimento.

- O número de tipos de instanciação genérica, ou *T*, em formato compactado de metadados ECMA.

- *T* tipos, cada uma representada em formato de assinatura de tipo ECMA.

A inclusão do comprimento de cada elemento de heap ativa a classificação simples da seção de diretório sem afetar o heap.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorDebugSymbolProvider2](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
