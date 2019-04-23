---
title: Criando uma classe para conter funções de DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399ad6649016e53d91d5d9d30ecc031ae8a97a4a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149351"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Criando uma classe para conter funções de DLL
O encapsulamento de uma função de DLL frequentemente usada em uma classe gerenciada é uma abordagem eficiente para encapsular a funcionalidade da plataforma. Embora não seja obrigatório fazer isso em todos os casos, o fornecimento de um wrapper de classe é conveniente, pois a definição de funções de DLL pode ser inconveniente e propensa a erros. Se você estiver programando no Visual Basic ou no C#, declare as funções de DLL em uma classe ou um módulo do Visual Basic.  
  
 Em uma classe, defina um método estático para cada função de DLL que você deseja chamar. A definição pode incluir informações adicionais, como o conjunto de caracteres ou a convenção de chamada usados para passar argumentos de método; ao omitir essas informações, selecione as configurações padrão. Para obter uma lista completa de opções de declaração e suas configurações padrão, consulte [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Depois de encapsular, você poderá chamar os métodos na classe da mesma forma em que chama métodos estáticos em qualquer outra classe. A invocação de plataforma manipula a função exportada subjacente automaticamente.  
  
 Ao criar uma classe gerenciada para a invocação de plataforma, considere as relações entre as classes e as funções de DLL. Por exemplo, você pode:  
  
-   Declare as funções de DLL em uma classe existente.  
  
-   Crie uma classe individual para cada função de DLL, mantendo as funções isoladas e fáceis de serem localizadas.  
  
-   Crie uma classe para um conjunto de funções de DLL relacionadas para formar agrupamentos lógicos e reduzir a sobrecarga.  
  
 Nomeie a classe e seus métodos conforme desejar. Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Consulte também

- [Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Identificando funções em DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Chamando uma função de DLL](../../../docs/framework/interop/calling-a-dll-function.md)
