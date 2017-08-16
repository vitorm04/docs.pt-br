---
title: 'Como: chamar APIs do Windows (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- API calls
- Windows API, calling
- API calls, platform invoke
- calls, stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e8df6609fa508eacd576c430df15c9f04551152
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-windows-apis-visual-basic"></a>Como chamar APIs do Windows (Visual Basic)
Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrInterop n º&1;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System>namespace.</xref:System>  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O método não é estático, é abstrato ou foi definido anteriormente. O tipo pai é uma interface, ou o comprimento de *nome* ou *dllName* é zero. (<xref:System.ArgumentException>)</xref:System.ArgumentException>  
  
-   The *name* or *dllName* is `Nothing`. (<xref:System.ArgumentNullException>)</xref:System.ArgumentNullException>  
  
-   O tipo recipiente foi criado anteriormente usando `CreateType`. (<xref:System.InvalidOperationException>)</xref:System.InvalidOperationException>  
  
## <a name="see-also"></a>Consulte também  
 [Invocação de plataforma examinar mais de perto](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [Exemplos de invocação de plataforma](http://msdn.microsoft.com/library/15926806-f0b7-487e-93a6-4e9367ec689f)   
 [Consumindo funções de DLL não gerenciada](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045)   
 [Definindo um método com reflexão emissão](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81)   
 [Passo a passo: Chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
