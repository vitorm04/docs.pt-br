---
title: Visão geral sobre interoperabilidade (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: d14c196babb03b7f13dde6ab5b46508a30ba26d6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43394524"
---
# <a name="interoperability-overview-c-programming-guide"></a>Visão geral sobre interoperabilidade (Guia de Programação em C#)
O tópico descreve métodos para permitir a interoperabilidade entre código gerenciado e código não gerenciado do C#.  
  
## <a name="platform-invoke"></a>Invocação de plataforma  
 A *invocação de plataforma* é um serviço que habilita o código gerenciado a chamar funções não gerenciadas que são implementadas em DLLs (bibliotecas de vínculo dinâmico), como aquelas na API do Win32 da Microsoft. Ela localiza e invoca uma função exportada e realiza marshaling dos argumentos (inteiros, cadeias de caracteres, matrizes, estruturas e assim por diante) além do limite de interoperação, conforme necessário.  
  
 Para obter mais informações, consulte [Consumindo funções de DLL não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md) e [Como usar a invocação de plataforma para reproduzir um arquivo wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  O [CLR](../../../standard/clr.md) (Common Language Runtime) gerencia o acesso aos recursos do sistema. Chamar código não gerenciado que esteja fora do CLR ignora esse mecanismo de segurança e, portanto, apresenta um risco de segurança. Por exemplo, o código não gerenciado pode chamar recursos diretamente em código não gerenciado, ignorando os mecanismos de segurança do CLR. Para obter mais informações, confira [Segurança no .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>Interoperabilidade C++  
 Você pode usar a interoperabilidade do C++, também conhecida como IJW (It Just Works), para encapsular uma classe de C++ nativa, de forma que ela possa ser consumida pelo código que é criado no C# ou em outra linguagem do .NET Framework. Para fazer isso, você deve escrever código C++ para encapsular um componente nativo DLL ou COM. Ao contrário de outras linguagens do .NET Framework, o [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] tem suporte de interoperabilidade que permite que o código gerenciado e não gerenciado seja localizado no mesmo aplicativo e até no mesmo arquivo. Então, você compila o código C++ usando a opção do compilador **/clr** para produzir um assembly gerenciado. Finalmente, você adiciona uma referência ao assembly no seu projeto do C# e usa os objetos encapsulados, assim como usaria outras classes gerenciadas.  
  
## <a name="exposing-com-components-to-c"></a>Expondo componentes COM ao C#  
 Você pode consumir um componente COM de um projeto do C#. As etapas gerais são as seguintes:  
  
1.  Localize um componente COM para usar e registre-o. Use regsvr32.exe para registrar ou cancelar o registro de uma DLL do COM.  
  
2.  Adicione ao projeto uma referência ao componente COM ou à biblioteca de tipo.  
  
     Quando você adiciona a referência, o Visual Studio usa o [Tlbimp.exe (Importador da biblioteca de tipos)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que usa uma biblioteca de tipos como entrada para produzir um assembly de interoperabilidade do .NET Framework. O assembly, também chamado de RCW (Runtime Callable Wrapper), contém classes gerenciadas e interfaces que encapsulam as classes COM e as interfaces que estão na biblioteca de tipos. O Visual Studio adiciona ao projeto uma referência ao assembly gerado.  
  
3.  Crie uma instância de uma classe que esteja definida no RCW. Isso, por sua vez, criará uma instância do objeto COM.  
  
4.  Use o objeto da mesma maneira que usa outros objetos gerenciados. Quando o objeto é recuperado pela coleta de lixo, a instância do objeto COM também é liberada da memória.  
  
 Para obter mais informações, consulte [Expondo componentes COM para o .NET Framework](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Expondo o C# para o COM  
 Os clientes COM podem consumir tipos do C# que foram expostos corretamente. As etapas básicas para expor os tipos do C# são as seguintes:  
  
1.  Adicione atributos de interoperabilidade no projeto do C#.  
  
     Você pode tornar visível um assembly COM ao modificar as propriedades do projeto do Visual C#. Para obter mais informações, consulte [Caixa de diálogo de informações do assembly](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Gere e registre uma biblioteca de tipos COM para ser usada pelo COM.  
  
     Você pode modificar as propriedades do projeto do Visual C# para registrar automaticamente o assembly do C# para a interoperabilidade COM. O Visual Studio usa a [Regasm.exe (ferramenta Assembly Registration)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), com a opção de linha de comando `/tlb`, que usa um assembly gerenciado como entrada para gerar uma biblioteca de tipos. Esta biblioteca de tipos descreve os tipos `public` no assembly e adiciona as entradas do Registro para que os clientes COM possam criar classes gerenciadas.  
  
 Para obter mais informações, consulte [Expondo componentes do .NET Framework para o COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) e [Classe COM de exemplo](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Melhorando o desempenho de interoperabilidade](https://msdn.microsoft.com/library/ms998551.aspx)  
 [Introdução à interoperabilidade entre COM e .NET](https://msdn.microsoft.com/library/office/bb610378.aspx)  
 [Introdução à interoperabilidade COM em Visual Basic](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 [Marshaling entre código gerenciado e não gerenciado](../../../../docs/framework/interop/interop-marshaling.md)  
 [Interoperação com código não gerenciado](../../../../docs/framework/interop/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
