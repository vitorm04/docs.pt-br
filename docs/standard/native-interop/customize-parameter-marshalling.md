---
title: Personalizar o marshalling de parâmetro - .NET
description: Saiba como personalizar a forma como o .NET realiza marshalling em seus parâmetros para uma representação nativa.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 7821da546e0ed0ab5fa97d00a638aa5cc1a3089c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411349"
---
# <a name="customizing-parameter-marshalling"></a>Personalizar o marshalling de parâmetro

Quando o comportamento de marshalling de parâmetro padrão do tempo de execução do .NET não fizer o que você deseja, use o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> para personalizar o modo como seus parâmetros passam pelo processo de marshalling.

## <a name="customizing-string-parameters"></a>Personalizar parâmetros de cadeias de caracteres

O .NET tem uma variedade de formatos para a realização de marshalling de cadeias de caracteres. Esses métodos são divididos em seções distintas em strings no C-style e em formatos de cadeias de caracteres centrados no Windows.

### <a name="c-style-strings"></a>Cadeias de caracteres C-style

Cada um desses formatos passa uma cadeia de caracteres terminada em nulo para o código nativo. Eles diferem pela codificação da cadeia de caracteres nativa.

| Valor `System.Runtime.InteropServices.UnmanagedType` | Codificando |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |

O formato <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> é um pouco diferente. Como `LPWStr`, ele realiza marshalling da cadeia de caracteres para uma cadeia de caracteres C-style nativa codificada em UTF-16. No entanto, a assinatura gerenciada passa a cadeia de caracteres por referência e a assinatura nativa correspondente usa a cadeia de caracteres por valor. Essa distinção permite que você use uma API nativa que recebe uma cadeia de caracteres por valor e a modifica no local sem precisar usar um `StringBuilder`. Recomendamos que você não use esse formato manualmente, pois ele pode causar confusão com as assinaturas nativas e gerenciadas incompatíveis.

### <a name="windows-centric-string-formats"></a>Formatos de cadeias de caracteres centradas no Windows

Ao interagir com interfaces COM ou OLE, você provavelmente descobrirá que as funções nativas tomam cadeias de caracteres como argumentos `BSTR`. Você pode usar o tipo não gerenciado <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> para realizar marshalling de uma cadeia de caracteres como um `BSTR`.

Se você estiver interagindo com as APIs do WinRT, poderá usar o formato <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> para realizar marshalling de uma cadeia de caracteres como `HSTRING`.

## <a name="customizing-array-parameters"></a>Personalizar parâmetros de matriz

.NET também fornece várias maneiras de realizar marshalling de parâmetros de matriz. Se você estiver chamando uma API que usa uma matriz C-style, use o tipo não gerenciado <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType>. Se os valores na matriz precisarem de marshalling personalizado, você poderá usar o campo <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> no atributo `[MarshalAs]` para isso.

Se você estiver usando APIs COM, provavelmente terá que organizar seus parâmetros de matriz como `SAFEARRAY*`s. Para fazer isso, você pode usar o tipo não gerenciado <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>. O tipo padrão dos elementos do `SAFEARRAY` pode ser visto na tabela sobre [ como personalizar campos `object`](./customize-struct-marshalling.md#marshalling-systemobjects). Você pode usar os campos <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> e <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> para personalizar o tipo de elemento exato do `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Personalizar parâmetros boolianos ou decimais

Para saber mais sobre como realizar marshalling de parâmetros boolianos ou decimais, consulte [Personalizar marshalling de estrutura](customize-struct-marshalling.md).

## <a name="customizing-object-parameters-windows-only"></a>Personalizar parâmetros de objeto (somente Windows)

No Windows, o tempo de execução do .NET fornece várias maneiras diferentes de realizar marshalling de parâmetros de objeto para código nativo.

### <a name="marshalling-as-specific-com-interfaces"></a>Marshalling como interfaces COM específicas

Se sua API leva um ponteiro para um objeto COM, você pode usar qualquer um dos seguintes formatos `UnmanagedType` em um parâmetro de tipo `object` para informar o .NET para realizar marshalling como essas interfaces específicas:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Além disso, se o seu tipo estiver marcado com `[ComVisible(true)]` ou se você estiver organizando o tipo `object`, poderá usar o formato <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> para realizar marshalling do seu objeto como um COM callable wrapper para a exibição COM do seu tipo.

### <a name="marshalling-to-a-variant"></a>Marshalling para uma `VARIANT`

Se sua API nativa tiver uma `VARIANT` Win32, você poderá usar o formato <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> no seu `object` para organizar seus objetos como `VARIANT`s. Consulte a documentação sobre [como personalizar campos `object`](customize-struct-marshalling.md#marshalling-systemobjects) para um mapeamento entre tipos .NET e tipos `VARIANT`.

### <a name="custom-marshalers"></a>Empacotadores personalizados

Se você deseja projetar uma interface COM nativa em um tipo gerenciado diferente, você pode usar o formato `UnmanagedType.CustomMarshaler` e uma implementação de <xref:System.Runtime.InteropServices.ICustomMarshaler> para fornecer seu próprio código de marshaling personalizado.
