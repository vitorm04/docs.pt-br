---
title: CLR (Common Language Runtime)
description: CLR (Common Language Runtime)
keywords: .NET, .NET Core
author: rpetrusha
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7704d9c9-e5fa-4969-a423-081cce0e21e6
translationtype: Human Translation
ms.sourcegitcommit: bb50b160a685d494ba47b3ca583f6fc35fa3ef3e
ms.openlocfilehash: 779b4bc43465833fa92e85d42156a232f390f7c2

---

# <a name="common-language-runtime-clr"></a>CLR (Common Language Runtime)

O .NET Framework fornece um ambiente de tempo de execução chamado Common Language Runtime, que executa o código e fornece serviços que facilitam o processo de desenvolvimento.

Compiladores e ferramentas expõem as funcionalidades do Common Language Runtime e permitem que você grave um código que se beneficia desse ambiente de execução gerenciado. O código que você desenvolve com um compilador de linguagem que visa o tempo de execução é chamado de código gerenciado. Ele aproveita recursos como integração em qualquer idioma, tratamento de exceções em qualquer idioma, segurança aprimorada, suporte a controle de versão e implantação, um modelo simplificado para interação entre componentes, além de serviços de depuração e criação de perfil.

> [!NOTE]
> Compiladores e ferramentas podem produzir saída que o Common Language Runtime pode consumir porque o sistema de tipos, o formato dos metadados e o ambiente de tempo de execução (o sistema virtual de execução) são todos definidos por um padrão público, a especificação Common Language Infrastructure ECMA. Para obter mais informações, consulte [Especificações ECMA C# e Common Language Infrastructure](https://www.visualstudio.com/en-us/mt639507).

Para habilitar o tempo de execução para fornecer serviços de código gerenciado, os compiladores de linguagem devem emitir metadados que descrevam os tipos, os membros e as referências em seu código. Os metadados são armazenados com o código. Todo arquivo PE (Portable Executable) do Common Language Runtime carregável contém metadados. O tempo de execução usa metadados para localizar e carregar classes, dispor instâncias na memória, resolver invocações de método, gerar código nativo, impor segurança e definir limites de contexto do tempo de execução.

O tempo de execução identifica automaticamente o layout de objeto e gerencia referências a objetos, liberando-os quando eles não estão sendo mais usados. Objetos cujos tempos de vida são gerenciados dessa forma são chamados de dados gerenciados. A coleta de lixo elimina perdas de memória, bem como alguns outros erros de programação comuns. Se o código for gerenciado, você poderá usar dados gerenciados, dados não gerenciados ou ambos no seu aplicativo do .NET Framework. Como os compiladores de linguagem fornecem seus próprios tipos, como tipos primitivos, você talvez sem sempre saiba (ou precise saber) se os dados estão sendo gerenciados.

O Common Language Runtime facilita a criação de componentes e aplicativos cujos objetos interagem entre linguagens. Objetos gravados em linguagens diferentes podem se comunicar entre si e seus comportamentos podem estar totalmente integrados. Por exemplo, você pode definir uma classe e usar uma linguagem diferente para derivar uma classe da classe original ou chamar um método na classe original. Você também pode passar uma instância de uma classe para um método de uma classe gravado em uma linguagem diferente. Essa integração em qualquer idioma é possível porque os compiladores de linguagens e ferramentas que segmentam o tempo de execução usam um Common Type System definido pelo tempo de execução e seguem as regras do tempo de execução para definir novos tipos, bem como para criar, usar, manter e associar a tipos.

Como parte de seus metadados, todos os componentes gerenciados transportam informações sobre os componentes e os recursos com base nos quais eles foram compilados. O tempo de execução usa essas informações para garantir que o componente ou o aplicativo tenha as versões especificadas de tudo o que precisa, o que torna seu código menos suscetível à interrupção devido a alguma dependência não atendida. As informações sobre os tipos que você define (e suas dependências) são armazenadas com o código como metadados, fazendo com que as tarefas de replicação do componente e remoção sejam muito menos complicadas.

Compiladores de linguagens e ferramentas expõem a funcionalidade do tempo de execução da maneira como seriam úteis e intuitivas para desenvolvedores. Isso significa que alguns recursos do tempo de execução devem ser mais perceptíveis em um ambiente do que em outro. Como você usa o tempo de execução depende de quais compiladores de linguagem ou ferramentas você usa. O tempo de execução oferece os seguintes benefícios: 

* A possibilidade de usar facilmente componentes desenvolvidos em outras linguagens.

* Tipos extensíveis fornecidos por uma biblioteca de classes.

* Recursos de linguagem como herança, interfaces e sobrecarga para programação orientada ao objeto.

* Suporte a threading livre explícito que permite a criação de aplicativos multithread, escalonáveis.

* Suporte ao tratamento de exceções estruturado.

* Suporte a atributos personalizados.

* Coleta de lixo.

* Uso de delegados em vez de ponteiros de função para maior segurança e segurança de tipos.

## <a name="versions-of-the-common-language-runtime"></a>Versões do Common Language Runtime

O número de versão do .NET Framework não corresponde necessariamente ao número de versão do CLR que ele inclui. A tabela a seguir mostra como os dois números de versão se correlacionam. 

Versão do .NET Framework | Inclui versão do CLR 
---------------------- | --------------------
1.0 | 1.0
1.1 | 1.1
2.0 | 2.0
3.0 | 2.0
3.5 | 2.0
4 | 4
4.5 (incluindo 4.5.1 e 4.5.2) | 4
4.6 (incluindo 4.6.1 e 4.6.2) | 4

## <a name="see-also"></a>Consulte também

[Gerenciamento Automático de Memória](garbagecollection/index.md)

 




<!--HONumber=Nov16_HO4-->


