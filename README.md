# Controle de Frequência

Sistema web de chamada e relatório mensal de presença, feito a pedido de uma assessoria esportiva de corrida.

> **Sobre este repositório:** o código não está publicado, porque o sistema foi feito para uso de um cliente. Aqui estão a descrição do projeto e um vídeo de demonstração. **O vídeo usa dados fictícios**: o nome e o logo da assessoria foram trocados, e os alunos foram inventados.

## Demonstração

https://github.com/user-attachments/assets/619a1e2f-5334-46cc-bab1-4a4b742b75e5

## O problema

A assessoria tem turmas de corrida em que cada aluno contrata um plano de 1 ou 2 treinos por semana. No fim do mês, era preciso saber quem treinou dentro do contratado, quem ficou acima e quem ficou abaixo.

A conta não é simples: há feriados, aulas canceladas e reposições, e há semanas que começam num mês e terminam no outro.

## A solução

Um sistema web, feito com Google Sheets e Apps Script, para o treinador usar no celular durante o treino.

**Como funciona:**

1. **Chamada:** o treinador abre a turma, marca quem veio e salva a chamada de uma vez.
2. **Dia sem aula:** se não houve treino, registra o motivo: feriado, aula cancelada ou aula transferida para outra data.
3. **Reposição:** uma aula cancelada pode ser reposta em outra data.
4. **Relatório do mês:** mostra cada aluno com o plano, as presenças e a situação (dentro, acima, abaixo ou a conferir).
5. **Relatório individual:** calendário de presenças e uma explicação do resultado, escrita pelo próprio sistema.
6. **PDF:** os relatórios da turma e de cada aluno saem em PDF, prontos para enviar.

**Regras que defini com a assessoria:**

- **O previsto nunca passa das aulas que aconteceram:** o previsto da semana é o menor valor entre o plano do aluno e as aulas realizadas. Feriado e aula cancelada não viram falta.
- **Reposição conta na semana original:** a presença numa aula reposta conta na semana em que a aula estava prevista, e não vira excesso.
- **Virada do mês:** uma semana que começa num mês e termina no outro é contada em um mês só, nunca em dois.
- **Mudança de plano:** se o aluno muda de 1x para 2x, a mudança vale a partir da semana atual, e o histórico anterior é mantido.
- **Avaliação provisória:** se falta registrar alguma chamada na semana, o resultado aparece como provisório até isso ser resolvido.
- **Desfazer:** excluir um aluno ou uma chamada pode ser desfeito por alguns minutos.

## O resultado

- A chamada e o fechamento do mês saem do mesmo lugar, sem conta manual.
- O relatório explica o resultado de cada aluno, por exemplo: "compareceu acima do contratado na Semana 1".
<!-- Confirme e ajuste a linha abaixo antes de publicar. -->
- **Status:** Iniciado os testes em outubro.


## Como construí

Construí o projeto com o apoio do Claude (IA da Anthropic). A divisão de papéis foi esta:

**O meu papel**
- Entender a rotina da assessoria e transformar a forma como ela trabalha em regras claras.
- Definir as regras de frequência: plano semanal, feriados, reposições e virada do mês.
- Desenhar as telas para uso no celular, durante o treino.
- Testar os casos que fogem do normal. Aqui usei a minha experiência anterior em QA.

**O papel da IA**
- Escrever o código a partir das minhas especificações.
- Sugerir soluções técnicas, como ler cada aba da planilha uma vez só por operação e proteger as gravações para duas pessoas não salvarem ao mesmo tempo.

O código foi escrito pela IA. As decisões sobre o que o sistema deve fazer, e a validação de que ele faz isso, foram minhas.

## Tecnologias

- **Google Sheets:** base de dados (turmas, alunos, planos, aulas e presenças)
- **Google Apps Script:** back-end e publicação como aplicativo web
- **HTML, CSS e JavaScript:** interface, com versão para celular e PDF para impressão
- **Claude (Anthropic):** apoio na escrita do código
