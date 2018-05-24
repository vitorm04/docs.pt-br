---
title: Marshaling de dados com invocação de plataforma
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eb55d8490eae64e909ada68223983c570ef9afa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-data-with-platform-invoke"></a>Marshaling de dados com invocação de plataforma
Para chamar funções exportadas de uma biblioteca não gerenciada, um aplicativo do .NET Framework requer um protótipo de função em código gerenciado que representa a função não gerenciada. Para criar um protótipo que habilita a invocação de plataforma a realizar marshaling de dados corretamente, você deve fazer o seguinte:  
  
-   Aplique o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> à função estática ou método em código gerenciado.  
  
-   Substitua os tipos de dados gerenciados por tipos de dados não gerenciados.  
  
 Você pode usar a documentação fornecida com uma função não gerenciada para construir um protótipo gerenciado equivalente, aplicando o atributo com os respectivos campos opcionais e substituindo os tipos de dados gerenciados por tipos não gerenciados. Para obter instruções sobre como aplicar o **DllImportAttribute**, consulte [Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Esta seção fornece amostras que demonstram como criar protótipos de função gerenciada para passar argumentos para e receber valores retornados de funções exportadas por bibliotecas não gerenciadas. As amostras também demonstram quando usar o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> e a classe <xref:System.Runtime.InteropServices.Marshal> para realizar marshaling de dados explicitamente.  
  
## <a name="platform-invoke-data-types"></a>Tipos de dados de invocação de plataforma  
 A tabela a seguir lista os tipos de dados usados na API do Win32 (listados em Wtypes.h) e funções de estilo C. Muitas bibliotecas não gerenciadas contêm funções que passam esses tipos de dados como parâmetros e valores retornados. A terceira coluna lista a classe ou tipo de valor interno correspondente do .NET Framework que você usa em código gerenciado. Em alguns casos, você pode substituir um tipo do mesmo tamanho pelo tipo listado na tabela.  
  
|Tipo não gerenciado em Wtypes.h|Tipo de linguagem C não gerenciado|Nome de classe gerenciada|Descrição|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**IDENTIFICADOR**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32 bits em Sistemas Operacionais Windows 32 bits, 64 bits em Sistemas Operacionais Windows 64 bits.|  
|**BYTE**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bits|  
|**SHORT**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bits|  
|**WORD**|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|16 bits|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 bits|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 bits|  
|**BOOL**|**long**|<xref:System.Byte>|32 bits|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Decore com ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Decore com Unicode.|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Decore com ANSI.|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Decore com ANSI.|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Decore com Unicode.|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Decore com Unicode.|  
|**FLOAT**|**Float**|<xref:System.Single?displayProperty=nameWithType>|32 bits|  
|**DOUBLE**|**Duplo**|<xref:System.Double?displayProperty=nameWithType>|64 bits|  
  
 Para tipos correspondentes em [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++, consulte a [Introdução à biblioteca de classes .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 O código a seguir define as funções de biblioteca fornecidas por Pinvoke.dll. Muitos exemplos descritos nesta seção chamam essa biblioteca.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
