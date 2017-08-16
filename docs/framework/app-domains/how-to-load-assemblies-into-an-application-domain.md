---
title: "Como carregar assemblies em um domínio do aplicativo | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7caaa27fed13c33508b7decde1d87e723167d96b
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Como carregar assemblies em um domínio de aplicativo
Há várias maneiras de carregar um assembly em um domínio de aplicativo. A maneira recomendada é usar o método <xref:System.Reflection.Assembly.Load%2A> `static` (`Shared` no Visual Basic) da classe [System.Reflection.Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx). Outras maneiras que os assemblies podem ser carregados incluem:  
  
-   O método <xref:System.Reflection.Assembly.LoadFrom%2A> da classe [Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) carrega um assembly dado seu local do arquivo. O carregamento de assemblies com esse método usa um contexto de carga diferente.  
  
-   Os métodos <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> e <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> carregam um assembly no contexto de somente reflexão. Os assemblies carregados neste contexto podem ser examinados, mas não executados, permitindo o exame dos assemblies que visam outras plataformas. Consulte [Como carregar assemblies no contexto de somente reflexão](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  O contexto de somente reflexão é uma novidade no .NET Framework versão 2.0.  
  
-   Métodos como <xref:System.AppDomain.CreateInstance%2A> e <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> da classe <xref:System.AppDomain> podem carregar assemblies em um domínio de aplicativo.  
  
-   O método <xref:System.Type.GetType%2A> da classe <xref:System.Type> pode carregar assemblies.  
  
-   O método <xref:System.AppDomain.Load%2A> da classe <xref:System.AppDomain?displayProperty=fullName> pode carregar assemblies, mas ele é usado principalmente para a interoperabilidade COM. Ele não deve ser usado para carregar assemblies em um domínio do aplicativo diferente do domínio do aplicativo do qual ele foi chamado.  
  
> [!NOTE]
>  A partir do .NET Framework versão 2.0, o tempo de execução não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o tempo de execução atualmente carregado. Isso vale para a combinação dos componentes principal e secundário do número de versão.  
  
 Você pode especificar a maneira como o JIT (Just-In-Time) compilou o código dos assemblies carregados é compartilhado entre os domínios do aplicativo. Para obter mais informações, consulte [Domínios do aplicativo e assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## <a name="example"></a>Exemplo  
 O código a seguir carrega um assembly chamado "example.exe" ou "example.dll" para o domínio de aplicativo atual, obtém um tipo chamado `Example` do assembly, obtém um método sem parâmetros chamado `MethodA` para esse tipo e executa o método. Para encontrar uma discussão completa sobre como obter as informações de um assembly carregado, consulte [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md) (Carregando e usando tipos dinamicamente).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)] [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)] [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 [Programação com domínios do aplicativo](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [Usando domínios do aplicativo](../../../docs/framework/app-domains/use.md)   
 [Como carregar assemblies no contexto de somente reflexão](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)   
 [Domínios do aplicativo e assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)
