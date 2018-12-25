# PZone RabbitMQ Logger

Windows service for writing RabbitMQ trace messages to MS SQL database.

## Logging Table
<table>
<tr><th>Column</th><th>Type</th><th>Description</th></tr>
<tr><td>id</td><td>uniqueidentifier</td><td>Идентификатор записи.</td></tr>
<tr><td>log_date</td><td>datetime</td><td>Дата добавления записи в лог.</td></tr>
<tr><td>host</td><td>varchar(50)</td><td>Хост брокера сообщений.</td></tr>
<tr><td>vhost</td><td>varchar(50)</td><td>Виртуальный хост брокера сообщений.</td></tr>
<tr><td>exchange</td><td>nvarchar(255)</td><td>Точка обмена, в которую поступило сообщение лога.</td></tr>
<tr><td>routing_key	nvarchar(255)</td><td>Ключ маршрутизации сообщения лога:<ul>
<li>сообщений, опубликованные в MB имеют ключ publish.</li>
<li>сообщения, считанные из MB имеют ключ <code>deliver.&lt;queue&gt;</code>, где <code>&lt;queue&gt;</code> — имя очереди, из которой забрали сообщение</li></ul></td></tr>
<tr><td>properties</td><td>nvarchar(2000)</td><td>Все параметры сообщения в формате JSON.</td></tr>
<tr><td>user</td><td>nvarchar(50)</td><td>Пользователь RMQ, от имени которого было опубликовано исходное сообщение.</td></tr>
<tr><td>routed_queues</td><td>nvarchar(255)</td><td>Список очередей (разделитель - запятая), в которые было отправлено исходное сообщение.</td></tr>
<tr><td>source_exchange</td><td>nvarchar(255)</td><td>Точка обмена, в которую было отправлено исходное сообщение.</td></tr>
<tr><td>source_routing_key</td><td>nvarchar(255)</td><td>Ключ маршрутизации исходного сообщения.</td></tr>
<tr><td>app_id</td><td>nvarchar(50)</td><td>Система, оправившая исходное сообщение.</td></tr>
<tr><td>message_id</td><td>nvarchar(50)</td><td>Идентификатор исходного сообщения.</td></tr>
<tr><td>correlation_id</td><td>nvarchar(50)</td><td>Идентификатор отслеживания исходного сообщения.</td></tr>
<tr><td>content_type</td><td>varchar(10)</td><td>Тип исходного сообщения.</td></tr>
<tr><td>content</td><td>ntext</td><td>Содержимое исходного сообщения.</td></tr>
<tr><td>timestamp</td><td>bigint</td><td>Timestamp публикации исходного сообщения.</td></tr>
</table>