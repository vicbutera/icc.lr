# Achados e Perdidos UFRPE: Documento de Requisitos
> Atividade prática de Levantamento de Requisitos (ICC / UFRPE).
> Atividade de prática: não é entregue e não vale nota.
## 1. Equipe
| Nome | Curso |
|------|-------|
| Victor Kauê Araújo da Silva | Ciência da Computação |

## 2. Visão geral
**Problema:** objetos perdidos no campus da UFRPE ficam espalhados entre
portarias, secretarias e grupos de mensagem, e raramente voltam ao dono.
**Solução proposta:**  aplicação permite o cadastro e a busca por itens perdidos no campus através de um sistema simples onde os usuários que acham os objetos cadastram-os no sistema com suas respectivas descrições, incluindo o local onde foram encontrados, e os usuários que perdem algum objeto tenham acesso a esses itens cadastrados no sistema e sejam capazes de alegar serem seus respectivos donos. Além disso, há a presença do usuário administrador, responsável pela confirmação da entrega e baixa no sistema.
**Escopo:** o sistema permite o cadastro de itens perdidos, a busca por esses itens, a elaboração de descrições para esses itens e que os usuários aleguem propriedade sobre os itens. O sistema não realiza entregas e não permite a comunicação em grupo entre usuários que alegam propriedade sobre os mesmos itens encontrados.
## 3. Atores (usuários do sistema)
| Ator | Descrição | O que precisa fazer |
|------|-----------|---------------------|
| Estudante | Aluno com matrícula ativa | Procurar objetos, registrar perdas |
| Servidor | Professor ou técnico | Agir como mediador em caso de disputas |
| Ponto de guarda | Portaria, biblioteca ou secretaria que guarda o objeto | Zelar o objeto durante o período em que ele não é encontrado, garantindo sua segurança |
| Administrador | Pessoa responsável pelo sistema | Confirmar as entregas e dar baixa no sistema |
## 4. Requisitos funcionais
Formato: código, nome, descrição, ator, prioridade e critérios de aceitação.
### RF01: Cadastrar objeto encontrado
- **Descrição:** o sistema deve permitir que um usuário registre um objeto
encontrado, informando categoria, descrição, cor, local, data e foto (opcional).
- **Ator:** Estudante, Servidor, Ponto de guarda
- **Prioridade:** Alta
- **Critérios de aceitação:**
- [ ] Os campos categoria, local e data são obrigatórios.
- [ ] O objeto aparece na busca logo após ser salvo.
- [ ] O sistema informa em qual ponto de guarda o objeto deve ser deixado.
### RF02: Buscar objetos
- **Descrição:** o sistema deve permitir buscar objetos por palavra-chave e
filtrar por categoria, campus/local e período.
- **Ator:** Todos
- **Prioridade:** Alta
- **Critérios de aceitação:**
- [ ] A busca por palavra-chave considera descrição, categoria e cor.
- [ ] Os filtros de categoria, campus/local e período podem ser combinados.
- [ ] Se nada for encontrado, o sistema exibe a mensagem "Nenhum objeto encontrado".
- [ ] Documentos oficiais aparecem sem foto (RN01).
### RF03: Registrar objeto perdido
- **Descrição:** o sistema deve permitir que um usuário registre um objeto
que perdeu, informando categoria, descrição, cor, local provável e data.
- **Ator:** Estudante, Servidor
- **Prioridade:** Média
- **Critérios de aceitação:**
- [ ] Os campos categoria, local e data são obrigatórios.
- [ ] O usuário consegue ver e editar a lista dos seus registros.
### RF04: Solicitar devolução (reivindicar objeto)
-- **Descrição:** o dono prova que o objeto é dele informando detalhes que só
ele conheceria (marca, conteúdo, marcas de uso etc.), sem que esses detalhes
estejam visíveis na descrição pública.
- **Ator:** Estudante, Servidor
- **Prioridade:** Alta
- **Critérios de aceitação:**
- [ ] O usuário preenche um formulário de comprovação ao reivindicar o objeto.
- [ ] A reivindicação fica "pendente" até ser analisada pelo administrador.
- [ ] Se houver mais de uma reivindicação para o mesmo objeto, um servidor é acionado para mediar.
### RF05: Notificar possível correspondência
- **Descrição:** o sistema deve avisar quem perdeu quando surgir um objeto
parecido, com categoria e cor iguais e local e data compatíveis.
- **Ator:** Estudante, Servidor
- **Prioridade:** Média
- **Critérios de aceitação:**
- [ ] A notificação é enviada por e-mail e exibida no sistema.
- [ ] A notificação leva ao item encontrado, sem exibir dados pessoais de terceiros.
### RF06: Registrar entrega ao dono
- **Descrição:** o administrador confirma que o objeto foi entregue ao dono
e dá baixa no sistema.
- **Ator:** Administrador
- **Prioridade:** Alta
- **Critérios de aceitação:**
- [ ] Só o administrador pode registrar a entrega.
- [ ] Após a baixa, o objeto sai da busca e fica no histórico com data e responsável.
### RF07: Autenticar usuário
- **Descrição:** o sistema deve permitir login com e-mail institucional e senha.
- **Ator:** Todos
- **Prioridade:** Alta
- **Critérios de aceitação:**
- [ ] Apenas e-mails institucionais (@ufrpe.br) são aceitos no cadastro.
- [ ] Cada perfil (estudante, servidor, ponto de guarda, administrador) vê só as funções que lhe cabem.
### RF08: Mediar disputas de reinvindicação
- **Descrição:** quando mais de uma pessoa alegar ser dona do mesmo objeto,
o servidor mediador analisa as comprovações e indica quem tem direito à devolução.
- **Ator:** Servidor, Administrador
- **Prioridade:** Média
- **Critérios de aceitação:**
- [ ] O servidor vê todas as reivindicações do objeto em disputa.
- [ ] A decisão fica registrada e é repassada ao administrador para a entrega.

## 5. Requisitos não funcionais
| Código | Categoria | Requisito | Como medir |
|--------|-----------|-----------|------------|
| RNF01 | Usabilidade | Funcionar em celular e computador | Testar em telas de 360 px a 1920 px |
| RNF02 | Desempenho | Busca responde rápido | Resultado em até 2 segundos |
| RNF03 | Segurança | <...> | <...> |
| RNF04 | Privacidade (LGPD) | Não exibir dados pessoais de terceiros | <...> |
| RNF05 | Acessibilidade | <...> | <...> |
| RNF06 | Disponibilidade | <...> | <...> |
## 6. Regras de negócio
- **RN01:** Documentos oficiais (RG, CNH, cartão) não têm foto publicada;
aparecem só como "documento encontrado".
- **RN02:** Objetos não retirados em <N> dias são <doados / descartados>.
- **RN03:** A retirada exige <documento com foto / confirmação de detalhes>.
- **RN04:** <...>
## 7. Histórias de usuário
- Como **estudante**, quero **buscar meu casaco pela cor e pelo local**,
para **saber se alguém o encontrou sem ir a todas as portarias**.
- Como **vigilante da portaria**, quero **<...>**, para **<...>**.
- Como **<ator>**, quero **<ação>**, para **<benefício>**.
## 8. Dúvidas em aberto
- [ ] Quem pode acessar: só a comunidade UFRPE ou o público em geral?
- [ ] Os objetos ficam guardados em um só lugar ou em vários pontos?
- [ ] <...>
