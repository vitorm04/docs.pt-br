---
title: "Visão geral sobre interoperabilidade (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c817dcd9073a5a1d4aeee558bf53d50566bbb472
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="interoperability-overview-c-programming-guide"></a>Visão geral sobre interoperabilidade (Guia de Programação em C#)
O tópico descreve métodos para permitir a interoperabilidade entre código gerenciado e código não gerenciado do C#.  
  
## <a name="platform-invoke"></a>Invocação de plataforma  
 A *invocação de plataforma* é um serviço que habilita o código gerenciado a chamar funções não gerenciadas que são implementadas em DLLs (bibliotecas de vínculo dinâmico), como aquelas na API do Win32 da Microsoft. Ela localiza e invoca uma função exportada e realiza marshaling dos argumentos (inteiros, cadeias de caracteres, matrizes, estruturas e assim por diante) além do limite de interoperação, conforme necessário.  
  
 Para obter mais informações, consulte [Consumindo funções de DLL não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md) e [Como usar a invocação de plataforma para reproduzir um arquivo wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  O [CLR](../../../standard/clr.md) (Common Language Runtime) gerencia o acesso aos recursos do sistema. Chamar código não gerenciado que esteja fora do CLR ignora esse mecanismo de segurança e, portanto, apresenta um risco de segurança. Por exemplo, o código não gerenciado pode chamar recursos diretamente em código não gerenciado, ignorando os mecanismos de segurança do CLR. Para obter mais informações, consulte [Segurança do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="c-interop"></a>Interoperabilidade C++  
 Você pode usar a interoperabilidade do C++, também conhecida como IJW (It Just Works), para encapsular uma classe de C++ nativa, de forma que ela possa ser consumida pelo código que é criado no C# ou em outra linguagem do .NET Framework. Para fazer isso, você deve escrever código C++ para encapsular um componente nativo DLL ou COM. Ao contrário de outras linguagens do .NET Framework, o [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] tem suporte de interoperabilidade que permite que o código gerenciado e não gerenciado seja localizado no mesmo aplicativo e até no mesmo arquivo. Então, você compila o código C++ usando a opção do compilador **/clr** para produzir um assembly gerenciado. Finalmente, você adiciona uma referência ao assembly no seu projeto do C# e usa os objetos encapsulados, assim como usaria outras classes gerenciadas.  
  
## <a name="exposing-com-components-to-c"></a>Expondo componentes COM ao C#  
 Você pode consumir um componente COM de um projeto do C#. As etapas gerais são as seguintes:  
  
1.  Localize um componente COM para usar e registre-o. Use regsvr32.exe para registrar ou cancelar o registro de uma DLL do COM.  
  
2.  Adicione ao projeto uma referência ao componente COM ou à biblioteca de tipo.  
  
     Quando você adiciona a referência, o [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] usa o [Tlbimp.exe (Importador da biblioteca de tipos)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), que utiliza uma biblioteca de tipos como entrada para produzir um assembly de interoperabilidade do .NET Framework. O assembly, também chamado de RCW (Runtime Callable Wrapper), contém classes gerenciadas e interfaces que encapsulam as classes COM e as interfaces que estão na biblioteca de tipos. O [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adiciona ao projeto uma referência ao assembly gerado.  
  
3.  Crie uma instância de uma classe que esteja definida no RCW. Isso, por sua vez, criará uma instância do objeto COM.  
  
4.  Use o objeto da mesma maneira que usa outros objetos gerenciados. Quando o objeto é recuperado pela coleta de lixo, a instância do objeto COM também é liberada da memória.  
  
 Para obter mais informações, consulte [Expondo componentes COM para o .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).  
  
## <a name="exposing-c-to-com"></a>Expondo o C# para o COM  
 Os clientes COM podem consumir tipos do C# que foram expostos corretamente. As etapas básicas para expor os tipos do C# são as seguintes:  
  
1.  Adicione atributos de interoperabilidade no projeto do C#.  
  
     Você pode tornar visível um assembly do COM ao modificar as propriedades de projeto do [!INCLUDE[csprcs](~/includes/csprcs-md.md)]. Para obter mais informações, consulte [Caixa de diálogo de informações do assembly](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Gere e registre uma biblioteca de tipos COM para ser usada pelo COM.  
  
     Você pode modificar as propriedades do projeto do [!INCLUDE[csprcs](~/includes/csprcs-md.md)] para registrar automaticamente o assembly do C# para a interoperabilidade COM. O [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] usa a [Regasm.exe (Ferramenta de Registro de Assembly)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb), usando a opção de linha de comando `/tlb`, que utiliza um assembly gerenciado como entrada, para gerar uma biblioteca de tipos. Esta biblioteca de tipos descreve os tipos `public` no assembly e adiciona as entradas do Registro para que os clientes COM possam criar classes gerenciadas.  
  
 Para obter mais informações, consulte [Expondo componentes do .NET Framework para o COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) e [Classe COM de exemplo](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Melhorando o desempenho de interoperabilidade](http://go.microsoft.com/fwlink/?LinkId=99564)   
 [Introdução à interoperabilidade COM](http://go.microsoft.com/fwlink/?LinkId=112406)   
 [Marshaling entre código gerenciado e não gerenciado](http://go.microsoft.com/fwlink/?LinkId=112398)   
 [Interoperação com código não gerenciado](https://msdn.microsoft.com/library/sd10k43k)   
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)

