---
title: "Manipulando exceções de interoperabilidade COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc3e01bc8ca463460ede9544d1d5c095c39a59d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="handling-com-interop-exceptions"></a>Manipulando exceções de interoperabilidade COM
Gerenciado e o código não gerenciado pode trabalhar juntos para lidar com exceções. Se um método lança uma exceção no código gerenciado, o common language runtime pode passar um HRESULT para um objeto COM. Se um método falhar no código não gerenciado retornando uma HRESULT de falha, o tempo de execução gera uma exceção que pode ser detectada pelo código gerenciado.  
  
 O tempo de execução automaticamente mapeia o HRESULT de interoperabilidade COM para exceções mais específicas. Por exemplo, E_ACCESSDENIED se torna <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se torna <xref:System.OutOfMemoryException>, e assim por diante.  
  
 Se o HRESULT for um resultado personalizado ou for desconhecido para o tempo de execução, o tempo de execução passa um genérico <xref:System.Runtime.InteropServices.COMException> ao cliente. O **ErrorCode** propriedade o **COMException** contém o valor HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Trabalhando com IErrorInfo  
 Quando um erro é passado de COM para código gerenciado, o tempo de execução preenche o objeto de exceção com informações de erro. Objetos COM que suportam IErrorInfo e retornam HRESULTS fornecem essas informações para exceções de código gerenciado. Por exemplo, o tempo de execução mapeia a descrição do erro COM a exceção <xref:System.Exception.Message%2A> propriedade. Se o HRESULT não fornece nenhuma informação de erro adicional, o tempo de execução preenche muitas das propriedades da exceção com valores padrão.  
  
 Se um método falhar no código não gerenciado, uma exceção pode ser passada para um segmento de código gerenciado. O tópico [HRESULTS e exceções](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contém uma tabela mostrando como HRESULTS mapeiam para objetos de exceção de tempo de execução.  

## <a name="see-also"></a>Consulte também
[Exceções](index.md) 
