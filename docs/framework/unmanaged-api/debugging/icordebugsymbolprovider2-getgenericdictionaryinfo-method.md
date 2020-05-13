---
title: 'Método ICorDebugSymbolProvider2:: GetGenericDictionaryInfo'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379317"
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
fora Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém o mapa de dicionário genérico. Para obter mais informações, consulte a seção Comentários.

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

onde o tamanho do diretório é `N * 8` .

O formato de cada item de informações de instanciação no heap é:

- O comprimento deste item de informações de instanciação em bytes no formato de metadados ECMA compactado. O valor exclui essas informações de comprimento.

- O número de tipos de instanciação genérica ou *T*, em formato de metadados ECMA compactado.

- Tipos *T* , cada um representado no formato de assinatura do tipo ECMA.

A inclusão do comprimento de cada elemento de heap permite a classificação simples da seção de diretório sem afetar o heap.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
