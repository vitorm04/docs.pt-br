---
title: Funções auxiliares Tlbexp (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104120"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Funções auxiliares Tlbexp (referência de API não gerenciada)
A [ferramenta Exportador da biblioteca de tipos](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll. Essa DLL contém duas funções auxiliares e uma interface que a ferramenta de exportação usa durante o processo de conversão de assembly para biblioteca de tipos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função GetTypeLibInfo](gettypelibinfo-function.md)  
 Fornece informações de localização e do sistema operacional para uma biblioteca de tipos.  
  
 [Função LoadTypeLibWithResolver](loadtypelibwithresolver-function.md)  
 Carrega uma biblioteca de tipos por meio de uma implementação da [interface ITypeLibResolver](itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciadas.  
  
 [Interface ITypeLibResolver](itypelibresolver-interface.md)  
 Fornece o [método ResolveTypeLib](resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.
