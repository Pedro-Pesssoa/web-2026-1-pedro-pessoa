# Sistema de Gestão de Contratação de Estagiários - UFERSA

## Descrição

Este projeto tem como objetivo desenvolver uma plataforma web para gerenciar o processo de contratação de estagiários não obrigatórios na UFERSA, automatizando etapas e centralizando informações.
O projeto foi desenvolvido como parte da avaliação da disciplina, sob a orientação do professor Walber Jose Adriano Silva, com o intuito de consolidar na prática os conceitos de engenharia de software, modelagem UML e arquitetura de sistemas distribuídos.

---

## Problema

A UFERSA realiza periodicamente a Contratação de Estagiários, processo mapeado na categoria Gestão de Pessoas do Portfólio de Processos (ep.ufersa.edu.br/portfolio). Atualmente, esse processo envolve múltiplos atores (discente, supervisor, setor de estágios, RH), troca de documentos em papel ou e-mail avulso, e ausência de rastreabilidade centralizada do status de cada solicitação.
O problema é que não existe um sistema web integrado que centralize as etapas de: abertura de vaga pelo supervisor, candidatura do discente, envio de documentação, análise pelo setor responsável, geração do termo de compromisso e notificação automática das partes. Isso gera retrabalho, demoras e perda de documentos.
Solução proposta: desenvolver uma aplicação web que digitalize e automatize o fluxo completo de contratação de estagiários da UFERSA, com acompanhamento em tempo real por todos os envolvidos e uso de IA generativa para triagem e auxílio documental.

---

## Perfis de Usuário

* Discente - Candidato à vaga de estágio; cadastra documentos e acompanha o processo
* Docente / Supervisor - Solicita abertura de vaga e acompanha o estagiário vinculado
* Técnico-Administrativo (RH) - Analisa documentação, aprova etapas e emite termos
* Coordenação - Preenche dados da empresa e assina termos digitalmente

---

## Informações a serem armazenadas

* Candidato/Discente: matrícula, CPF, nome completo, curso, período, contato, histórico escolar, currículo.
* Vaga de estágio: descrição da vaga, carga horária, período, supervisor responsável, setor/empresa concedente, status (aberta / em análise / preenchida / encerrada).
* Documentação: termo de compromisso, apólice de seguro, declaração de matrícula, plano de atividades, relatórios de estágio parciais e final.
* Processo: histórico de status com datas e responsável por cada transição, observações e pareceres, assinaturas digitais.
* Notificações: log de e-mails e alertas enviados, com timestamp e destinatário.

---

## Arquitetura do sistema

* [Estimativa de custos AWS](https://calculator.aws/#/estimate?id=2c179daa74b54c5fe5f9fa5afaa7ac54b6cf3ffb)

![Arquitetura do Sistema](./docs/arquitetura)

O usuário acessa o sistema pelo domínio registrado no Route 53, que direciona para dois destinos: o S3 (serve o frontend Next.js estático) e o API Gateway (recebe as chamadas da API). O API Gateway repassa as requisições ao EC2 rodando o backend Django. O backend então persiste os dados das vagas, processos e usuários no DynamoDB, salva os arquivos e documentos PDF no S3 de documentos, dispara e-mails de notificação via SES e chama a Claude API para as funcionalidades de IA generativa.

---

## 🤖 Uso de IA

O sistema utilizará IA generativa para:

* Análise de candidaturas


## 🔗 Repositório

Nome: **web-2026-1-pedro-pessoa**

---

## 👨‍💻 Autor

Pedro Pessoa

---

## 📌 Status

🚧 Em desenvolvimento
