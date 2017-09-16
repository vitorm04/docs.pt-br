---
title: "Tipos blittable e não blittable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: 23
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3fa97ee1df14b5e08faa944265675264c0b6d95a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="blittable-and-non-blittable-types"></a>Tipos blittable e não blittable
A maioria dos tipos de dados tem uma representação comum na memória gerenciada e não gerenciada e não exige manipulação especial pelo marshaler de interoperabilidade. Esses tipos são chamados *tipos blittable* porque não exigem conversão quando são passados entre o código gerenciado e não gerenciado.  
  
 Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos blittable. A invocação de plataforma não dá suporte a estruturas não blittable como tipos de retorno.  
  
 Os seguintes tipos do namespace <xref:System> são tipos blittable:  
  
-   <xref:System.Byte?displayProperty=fullName>  
  
-   <xref:System.SByte?displayProperty=fullName>  
  
-   <xref:System.Int16?displayProperty=fullName>  
  
-   <xref:System.UInt16?displayProperty=fullName>  
  
-   <xref:System.Int32?displayProperty=fullName>  
  
-   <xref:System.UInt32?displayProperty=fullName>  
  
-   <xref:System.Int64?displayProperty=fullName>  
  
-   <xref:System.UInt64?displayProperty=fullName>  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Single?displayProperty=fullName>  
  
-   <xref:System.Double?displayProperty=fullName>  
  
 Os seguintes tipos complexos também são tipos blittable:  
  
-   Matrizes unidimensionais de tipos blittable, como uma matriz de inteiros. No entanto, um tipo que contém uma matriz variável de tipos blittable não é blittable em si.  
  
-   Tipos de valor formatados que contêm somente tipos blittable (e classes, se elas tiverem o marshaling realizado como tipos formatados). Para obter mais informações sobre os tipos de valor formatados, consulte [Marshaling padrão para tipos de valor](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).  
  
 Referências de objeto não são blittable. Isso inclui uma matriz de referências a objetos que são blittable por si mesmos. Por exemplo, é possível definir uma estrutura blittable, mas não é possível definir um tipo blittable que contém uma matriz de referências a essas estruturas.  
  
 Como uma otimização, as matrizes de tipos blittable e as classes que contêm somente membros blittable são [fixadas](../../../docs/framework/interop/copying-and-pinning.md), em vez de copiadas durante o marshaling. Esses tipos podem parecer como se tivessem o marshaling realizado como parâmetros de Entrada/Saída quando o chamador e o receptor estão no mesmo apartment. No entanto, esses tipos, na verdade, têm o marshaling realizado como parâmetros de Entrada e é necessário aplicar os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> de você desejar realizar marshaling do argumento como um parâmetro de Entrada/Saída.  
  
 Alguns tipos de dados gerenciados exigem uma representação diferente em um ambiente não gerenciado. Esses tipos de dados não blittable devem ser convertidos em um formato que pode ter o marshaling realizado. Por exemplo, cadeias de caracteres gerenciadas não são tipos blittable porque devem ser convertidas em objetos de cadeia de caracteres antes que possam ter o marshaling realizado.  
  
 A tabela a seguir lista tipos não blittable do namespace <xref:System>. [Representantes](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), que são estruturas de dados que se referem a um método estático ou a uma instância de classe, também não são blittable.  
  
|Tipo não bittable|Descrição|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Converte em uma matriz C-style ou em um `SAFEARRAY`.|  
|[System.Boolean](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|Converte em um valor de 1, 2 ou 4 bytes com `true` como 1 ou -1.|  
|[System.Char](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|Converte em um caractere Unicode ou ANSI.|  
|[System.Class](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|Converte em uma interface de classe.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Converte em uma variante ou uma interface.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Converte em uma matriz C-style ou em um `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Converte em uma cadeia de caracteres que termina em uma referência nula ou em um BSTR.|  
|[System.Valuetype](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|Converte em uma estrutura com um layout de memória fixo.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Converte em uma matriz C-style ou em um `SAFEARRAY`.|  
  
 Há suporte para tipos de objeto e de classe apenas na interoperabilidade COM. Para tipos correspondentes no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++, consulte a [Visão geral da biblioteca de classes](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Comportamento de marshaling padrão](../../../docs/framework/interop/default-marshaling-behavior.md)

