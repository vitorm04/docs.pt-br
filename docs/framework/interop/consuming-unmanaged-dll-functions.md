---
title: "Consumindo funções de DLL não gerenciadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd1e5f4fc03da2310022efdeb4530440b5e07f3d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="consuming-unmanaged-dll-functions"></a>Consumindo funções de DLL não gerenciadas
A invocação de plataforma é um serviço que permite que um código gerenciado chame funções não gerenciadas implementadas em DLLs (bibliotecas de vínculo dinâmico), como aquelas na API do Win32. Ela localiza e invoca uma função exportada e realiza marshaling dos argumentos (inteiros, cadeias de caracteres, matrizes, estruturas e assim por diante) além do limite de interoperação, conforme necessário. Para obter mais informações sobre esse serviço, consulte [Visão aprofundada da invocação de plataforma](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).  
  
 Esta seção apresenta várias tarefas associadas ao consumo de funções de DLL não gerenciadas. Além das tarefas a seguir, há considerações gerais e um link que fornece exemplos e informações adicionais.  
  
#### <a name="to-consume-exported-dll-functions"></a>Para consumir funções de DLL exportadas  
  
1.  [Identifique as funções nas DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     No mínimo, é necessário especificar o nome da função e o nome da DLL que ela contém.  
  
2.  [Crie uma classe para conter funções de DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Use uma classe existente, crie uma classe individual para cada função não gerenciada ou crie uma classe que contém um conjunto de funções não gerenciadas relacionadas.  
  
3.  [Crie protótipos em um código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Use a instrução **Declare** com as palavras-chave **Function** e **Lib**. Em alguns casos raros, é possível usar o **DllImportAttribute** com as palavras-chave **Shared Function**. Esses casos são explicados mais adiante nesta seção.  
  
     [C#] Use o **DllImportAttribute** para identificar a DLL e a função. Marque o método com os modificadores **static** e **extern**.  
  
     [C++] Use o **DllImportAttribute** para identificar a DLL e a função. Marque o método wrapper ou a função com **extern "C"**.  
  
4.  [Chame uma função de DLL](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Chame o método na classe gerenciada como faria com qualquer outro método gerenciado. [Passar estruturas](../../../docs/framework/interop/passing-structures.md) e [implementar funções de retorno de chamada](../../../docs/framework/interop/callback-functions.md) são casos especiais.  
  
 Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Visão aprofundada da invocação de plataforma  
 A invocação de plataforma se baseia nos metadados para localizar funções exportadas e realizar marshaling em seus argumentos em tempo de execução. A ilustração a seguir mostra esse processo.  
  
 ![Invocação de plataforma](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")  
Uma chamada da invocação de plataforma a uma função de DLL não gerenciada  
  
 Quando uma invocação de plataforma chama uma função não gerenciada, ela executa a seguinte sequência de ações:  
  
1.  Localiza a DLL que contém a função.  
  
2.  Carrega a DLL na memória.  
  
3.  Localiza o endereço da função na memória e efetua push de seus argumentos para a pilha, realizando marshaling dos dados, conforme necessário.  
  
    > [!NOTE]
    >  A localização e o carregamento da DLL, bem como a localização do endereço da função na memória, ocorrem apenas na primeira chamada à função.  
  
4.  Transfere o controle para a função não gerenciada.  
  
 A invocação de plataforma gera exceções geradas pela função não gerenciada para o chamador gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)  
 [Exemplos de invocação de plataforma](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)  
 [Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
