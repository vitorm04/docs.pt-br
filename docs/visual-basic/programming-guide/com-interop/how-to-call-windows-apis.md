---
title: 'Como: Chamar APIs do Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: e7b76495b83cb9a1dfe7629a1d82695d2046eac2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972762"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Como: Chamar APIs do Windows (Visual Basic)
Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System> namespace.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O método não é estático, é abstrato ou foi definido anteriormente. O tipo pai é uma interface ou o comprimento da *nome* ou *dllName* é zero. (<xref:System.ArgumentException>)  
  
-   O *nome* ou *dllName* é `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   O tipo recipiente foi criado anteriormente usando `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Consulte também

- [Um olhar detalhado sobre invocação de plataforma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Exemplos de invocação de plataforma](../../../framework/interop/platform-invoke-examples.md)
- [Consumindo funções de DLL não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Emissão de definição de um método com reflexão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Passo a passo: fazer chamadas de APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
