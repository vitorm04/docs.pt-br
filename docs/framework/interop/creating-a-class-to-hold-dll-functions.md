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
ms.openlocfilehash: 765d4344553a6e65b930a7bf586a41144d220fc6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123630"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Criando uma classe para conter funções de DLL
O encapsulamento de uma função de DLL frequentemente usada em uma classe gerenciada é uma abordagem eficiente para encapsular a funcionalidade da plataforma. Embora não seja obrigatório fazer isso em todos os casos, o fornecimento de um wrapper de classe é conveniente, pois a definição de funções de DLL pode ser inconveniente e propensa a erros. Se você estiver programando no Visual Basic ou no C#, declare as funções de DLL em uma classe ou um módulo do Visual Basic.  
  
 Em uma classe, defina um método estático para cada função de DLL que você deseja chamar. A definição pode incluir informações adicionais, como o conjunto de caracteres ou a convenção de chamada usados para passar argumentos de método; ao omitir essas informações, selecione as configurações padrão. Para obter uma lista completa de opções de declaração e suas configurações padrão, consulte [Criando protótipos em código gerenciado](creating-prototypes-in-managed-code.md).  
  
 Depois de encapsular, você poderá chamar os métodos na classe da mesma forma em que chama métodos estáticos em qualquer outra classe. A invocação de plataforma manipula a função exportada subjacente automaticamente.  
  
 Ao criar uma classe gerenciada para a invocação de plataforma, considere as relações entre as classes e as funções de DLL. Por exemplo, você pode:  
  
- Declare as funções de DLL em uma classe existente.  
  
- Crie uma classe individual para cada função de DLL, mantendo as funções isoladas e fáceis de serem localizadas.  
  
- Crie uma classe para um conjunto de funções de DLL relacionadas para formar agrupamentos lógicos e reduzir a sobrecarga.  
  
 Nomeie a classe e seus métodos conforme desejar. Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Consulte também

- [Consumindo funções de DLL não gerenciadas](consuming-unmanaged-dll-functions.md)
- [Identificando funções em DLLs](identifying-functions-in-dlls.md)
- [Criando protótipos em código gerenciado](creating-prototypes-in-managed-code.md)
- [Chamando uma função de DLL](calling-a-dll-function.md)
