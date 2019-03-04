---
title: 'Como: converter uma matriz de bytes em um int – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 3563b0ffd5360c575404ead81e0e847ccab46f0c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972424"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Como: converter uma matriz de bytes em um int (Guia de Programação em C#)
Este exemplo mostra como usar a classe <xref:System.BitConverter> para converter uma matriz de bytes em um [int](../../../csharp/language-reference/keywords/int.md) e de volta em uma matriz de bytes. Talvez você precise converter bytes em um tipo de dados interno depois de ler bytes da rede, por exemplo. Além do método [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) no exemplo, a tabela a seguir lista métodos na classe <xref:System.BitConverter> convertem bytes (de uma matriz de bytes) em outros tipos internos.  
  
|Tipo retornado|Método|  
|-------------------|------------|  
|`bool`|[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Exemplo  
 Este exemplo inicializa uma matriz de bytes, reverte a matriz se a arquitetura do computador for little endian (ou seja, se o byte menos significativo for armazenado primeiro) e, em seguida, chama o método [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) para converter quatro bytes da matriz em um `int`. O segundo argumento para [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) especifica o índice de início da matriz de bytes.  
  
> [!NOTE]
>  A saída pode ser diferente dependendo do quanto a arquitetura do computador é endian.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o método <xref:System.BitConverter.GetBytes%28System.Int32%29> da classe <xref:System.BitConverter> é chamado para converter um `int` em uma matriz de bytes.  
  
> [!NOTE]
>  A saída pode ser diferente dependendo do quanto a arquitetura do computador é endian.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Tipos](../../../csharp/programming-guide/types/index.md)
