---
title: Realizando marshaling de cadeias de caracteres
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
ms.workload:
- dotnet
ms.openlocfilehash: adcdf55f3e33a48c4fd10ea243bb0ce3497f522f
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-strings"></a>Realizando marshaling de cadeias de caracteres
A invocação de plataforma copia parâmetros de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado (ANSI), se necessário. Já que as cadeias de caracteres gerenciadas são imutáveis, a invocação de plataforma não as copia de volta da memória não gerenciada para a memória gerenciada quando a função retorna.  
  
 A tabela a seguir lista as opções de marshaling para cadeias de caracteres, descreve o uso delas e fornece um link para a amostra de .NET Framework correspondente.  
  
|Cadeia de Caracteres|Descrição|Amostra|  
|------------|-----------------|------------|  
|Por valor.|Passa cadeias de caracteres como parâmetros In.|[MsgBox](msgbox-sample.md)|  
|Como resultado.|Retorna cadeias de caracteres de código não gerenciado.|[Cadeias de Caracteres](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Por referência.|Passa cadeias de caracteres como parâmetros In/Out usando <xref:System.Text.StringBuilder>.|[Buffers](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|Em uma estrutura por valor.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In.|[Estruturas](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|Em uma estrutura por referência **(char\*)**.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um ponteiro para um buffer de caracteres e o tamanho do buffer é um membro da estrutura.|[Cadeias de Caracteres](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Em uma estrutura por referência **(char[])**.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Em uma classe por valor **(char\*)**.|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um ponteiro para um buffer de caracteres.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|Em uma classe por valor **(char[])**.|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Como uma matriz de cadeias de caracteres por valor.|Cria uma matriz de cadeias de caracteres que é passada por valor.|[Matrizes](marshaling-different-types-of-arrays.md)|  
|Como uma matriz de estruturas que contêm cadeias de caracteres por valor.|Cria uma matriz de estruturas que contêm cadeias de caracteres e a matriz é transmitida por valor.|[Matrizes](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Marshaling de dados com a invocação de plataforma](marshaling-data-with-platform-invoke.md)  
 [Tipos de dados de invocação de plataforma](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Marshaling de classes, estruturas e uniões](marshaling-classes-structures-and-unions.md)  
 [Marshaling de matrizes de tipos](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Exemplos diversos de marshaling](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
