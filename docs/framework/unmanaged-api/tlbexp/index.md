---
title: Funções auxiliares Tlbexp (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967694"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Funções auxiliares Tlbexp (referência de API não gerenciada)
A [ferramenta Exportador da biblioteca de tipos](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll. Essa DLL contém duas funções auxiliares e uma interface que a ferramenta de exportação usa durante o processo de conversão de assembly para biblioteca de tipos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função GetTypeLibInfo](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 Fornece informações de localização e do sistema operacional para uma biblioteca de tipos.  
  
 [Função LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 Carrega uma biblioteca de tipos por meio de uma implementação da [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciadas.  
  
 [Interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 Fornece o [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.
