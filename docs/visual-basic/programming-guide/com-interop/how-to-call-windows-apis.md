---
title: Como chamar APIs do Windows (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: de568c3273d4d040c6566136e5d59e2155b86f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Como chamar APIs do Windows (Visual Basic)
Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System> namespace.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O método não é estático, é abstrato ou foi definido anteriormente. O tipo pai é uma interface ou o comprimento de *nome* ou *Nomedadll* é zero. (<xref:System.ArgumentException>)  
  
-   O *nome* ou *Nomedadll* é `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   O tipo recipiente foi criado anteriormente usando `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Consulte também  
 [Um olhar detalhado sobre invocação de plataforma](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Exemplos de invocação de plataforma](../../../framework/interop/platform-invoke-examples.md)  
 [Consumindo funções de DLL não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Emissão de definição de um método com reflexão](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
