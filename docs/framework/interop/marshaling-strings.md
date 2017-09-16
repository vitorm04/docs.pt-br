---
title: Realizando marshaling de cadeias de caracteres
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
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8d8455d4f1b4dbb463176c06d680b2bd0b1ff9d9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-strings"></a>Realizando marshaling de cadeias de caracteres
A invocação de plataforma copia parâmetros de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado (ANSI), se necessário. Já que as cadeias de caracteres gerenciadas são imutáveis, a invocação de plataforma não as copia de volta da memória não gerenciada para a memória gerenciada quando a função retorna.  
  
 A tabela a seguir lista as opções de marshaling para cadeias de caracteres, descreve o uso delas e fornece um link para a amostra de .NET Framework correspondente.  
  
|Cadeia de caracteres|Descrição|Amostra|  
|------------|-----------------|------------|  
|Por valor.|Passa cadeias de caracteres como parâmetros In.|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|Como resultado.|Retorna cadeias de caracteres de código não gerenciado.|[Cadeias de Caracteres](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Por referência.|Passa cadeias de caracteres como parâmetros In/Out usando <xref:System.Text.StringBuilder>.|[Buffers](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|Em uma estrutura por valor.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In.|[Estruturas](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|Em uma estrutura por referência **(char\*)**.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um ponteiro para um buffer de caracteres e o tamanho do buffer é um membro da estrutura.|[Cadeias de Caracteres](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Em uma estrutura por referência **(char[])**.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Em uma classe por valor **(char\*)**.|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um ponteiro para um buffer de caracteres.|[OpenFileDlg](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|Em uma classe por valor **(char[])**.|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Como uma matriz de cadeias de caracteres por valor.|Cria uma matriz de cadeias de caracteres que é passada por valor.|[Matrizes](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Como uma matriz de estruturas que contêm cadeias de caracteres por valor.|Cria uma matriz de estruturas que contêm cadeias de caracteres e a matriz é transmitida por valor.|[Matrizes](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Tipos de Dados de Invocação de Plataforma](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Marshaling de classes, estruturas e uniões](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)   
 [Marshaling de matrizes de tipos](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)   
 [Exemplos diversos de marshaling](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)

