---
title: 'Método ICorDebugSymbolProvider2:: GetGenericDictionaryInfo'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: c9f7206cac54d64c28eb50d81fea00a6f3c494d4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133627"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Método ICorDebugSymbolProvider2:: GetGenericDictionaryInfo

Recupera um mapa de dicionário genérico.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Parâmetros

`ppMemoryBuffer`\
fora Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) que contém o mapa de dicionário genérico. Consulte a seção Comentários para obter mais informações.

## <a name="remarks"></a>Comentários

> [!NOTE]
> Esse método está disponível somente com .NET Native.

O mapa consiste em duas seções de nível superior:

- Um [diretório](#Directory) que contém os endereços virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.

- Um [heap](#Heap) alinhado em byte que contém informações de instanciação de objeto. Ele começa imediatamente após a última entrada de diretório.

<a name="Directory"></a>

## <a name="the-directory"></a>O diretório

Cada entrada no diretório refere-se a um deslocamento dentro do heap; ou seja, é um deslocamento relativo ao início do heap. O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontem para o mesmo deslocamento no heap.

A parte do diretório do mapa de dicionário genérico tem a seguinte estrutura:

- Os quatro primeiros bytes contêm o número de entradas de dicionário (ou seja, o número de endereços virtuais relativos no dicionário). Iremos nos referir a esse valor como *N*. Se o bit alto for definido, as entradas serão classificadas por endereço virtual relativo em ordem crescente.

- As entradas *N* diretório seguem. Cada entrada consiste em 8 bytes, em dois segmentos de 4 bytes:

  - Bytes 0-3: RVA; o endereço virtual relativo do dicionário.

  - Bytes 4-7: offset; um deslocamento relativo ao início do heap.

<a name="Heap"></a>

## <a name="the-heap"></a>O heap

O tamanho do heap pode ser calculado por um leitor de fluxo subtraindo o comprimento do fluxo do tamanho do diretório + 4. Em outras palavras:

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

onde o tamanho do diretório é `N * 8`.

O formato de cada item de informações de instanciação no heap é:

- O comprimento deste item de informações de instanciação em bytes no formato de metadados ECMA compactado. O valor exclui essas informações de comprimento.

- O número de tipos de instanciação genérica ou *T*, em formato de metadados ECMA compactado.

- Tipos *T* , cada um representado no formato de assinatura do tipo ECMA.

A inclusão do comprimento de cada elemento de heap permite a classificação simples da seção de diretório sem afetar o heap.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorDebugSymbolProvider2](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
