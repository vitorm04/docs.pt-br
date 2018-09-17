---
title: Manipulando exceções de interoperabilidade COM
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45590946"
---
# <a name="handling-com-interop-exceptions"></a>Manipulando exceções de interoperabilidade COM
Os códigos gerenciado e não gerenciado podem trabalhar juntos para tratar de exceções. Se um método lança uma exceção no código gerenciado, o common language runtime pode passar um HRESULT para um objeto COM. Se um método falhar no código não gerenciado, retornando um HRESULT de falha, o tempo de execução lançará uma exceção que pode ser detectada pelo código gerenciado.  
  
 O tempo de execução mapeia automaticamente o HRESULT da interoperabilidade COM para exceções mais específicas. Por exemplo, E_ACCESSDENIED se torna <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se torna <xref:System.OutOfMemoryException> e assim por diante.  
  
 Se o HRESULT for um resultado personalizado, ou se for desconhecido para o tempo de execução, o tempo de execução passará um <xref:System.Runtime.InteropServices.COMException> genérico ao cliente. A propriedade **ErrorCode** do **COMException** contém o valor de HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Trabalhar com IErrorInfo  
 Quando um erro é passado do COM para o código gerenciado, o tempo de execução preenche o objeto de exceção com informações do erro. Objetos COM que dão suporte a IErrorInfo e retornam HRESULTS fornecem essas informações para exceções de código gerenciado. Por exemplo, o tempo de execução mapeia a Descrição do erro COM para a propriedade <xref:System.Exception.Message%2A> da exceção. Se o HRESULT não fornecer mais informações sobre o erro, o tempo de execução preencherá muitas das propriedades da exceção com valores padrão.  
  
 Se um método falhar no código não gerenciado, uma exceção poderá ser passada para um segmento de código gerenciado. O tópico [HRESULTS e exceções](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contém uma tabela que mostra como HRESULTS mapeia para objetos de exceção de tempo de execução.  

## <a name="see-also"></a>Consulte também

- [Exceções](index.md)
