# Middleware

This is a guide on how to install the necessary middleware for running the Universal Queue Management Application on your local machine.

# What's there to install

For this current version of the application to run on your local host, you'll need to install the following:

* RabbitMQ
* MongoDB

## Installing RabbitMQ on Windows

In order to install RabbitMQ, there a couple of methods which we'll be covering.

### Using Chocolatey

This option is not guaranteed to provide the latest release. It does, however, manage the required dependencies.

To install RabbitMQ using Chocolatey, run the following command from the _command line_ or from _PowerShell_:
```
choco install rabbitmq
```

### Using the Installer (Tested)

**Installing dependencies (Erlang 23.1.1)**

RabbitMQ requires a 64-bit supported version of Erlang for Windows to be installed. A list of which Erlang version for which RabbitMQ version can be found [here](https://www.rabbitmq.com/which-erlang.html), and the latest binary builds for Windows can be obtained from the [Erlang/OTP Version Tree](https://erlang.org/download/otp_versions_tree.html) page.

As an example, here's how to install `Erlang 23.1.1` using the 64-bit Windows installer:
```
# Step 1 - Download the installer
https://github.com/erlang/otp/releases/download/OTP-23.1.1/otp_win64_23.1.1.exe

# Step 2 - Run the installer (.exe file) as Administrator

# Step 3 - Follow the installer's instructions
```

**Installing RabbitMQ (RabbitMQ 3.8.9)**

Once a supported version of Erlang is installed, download the compatible RabbitMQ installer, `rabbitmq-server-{version}.exe` and run it. It installs RabbitMQ as a _Windows service_ and starts it using the _default configuration_ ([details](https://www.rabbitmq.com/install-windows.html#default-user-access)). 

For a full list of RabbitMQ releases, refer to this [page](https://github.com/rabbitmq/rabbitmq-server/releases).

As an example, here's how to install `RabbitMQ 3.8.9` using the Windows installer:
```
# Step 1 - Download the installer
https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.8.9/rabbitmq-server-3.8.9.exe

# Step 2 - Run the installer (.exe file) as Administrator

# Step 3 - Follow the installer's instructions
```

* Once both Erlang and RabbitMQ have been installed, a RabbitMQ node can be started as a Windows service. The RabbitMQ service starts automatically. RabbitMQ Windows service ca be managed from the Start menu.

* Firewalls and security tools can prevent RabbitMQ Windows service and CLI tools from operating correctly. If that happens, configure those tools to whitelist access to [ports used by RabbitMQ](https://www.rabbitmq.com/install-windows.html#ports).

### Default User Access 

The broker creates a _user_ `guest` with _password_ `guest`. Unconfigured clients will in general use these credentials. **By default, these credentials can only be used when connecting to the broker as localhost** so you will need to take action before connecting from any other machine ([details](https://www.rabbitmq.com/access-control.html)).

**Note**
You can access RabbitMQ's management UI via `localhost:15672` using the default `guest` user.

## Installing Community MongoDB on Widows 

The following installs MongoDB 4.4 Community Edition, which supports the following 64-bit versions of Windows:
Windows 10, Windows Server 2019, and Windows Server 2016.

### Download the installer

Download the MongoDB Community .msi [installer ](https://www.mongodb.com/try/download/community?tck=docs_server)
```
a. In the Version dropdown, select version 4.4.4 of MongoDB.

b. In the Platform dropdown, select Windows.

c. In the Package dropdown, select msi.

d. Click Download.
```

### Run the MongoDB installer

```
a. Go to the directory where you downloaded the MongoDB installer (.msi file). By default, this is your Downloads directory.
b. Double-click the .msi file.
```

### Follow the MongoDB Community Edition installation wizard

1. **Choose Setup Type:** You can choose either the Complete (recommended for most users) or Custom setup type. The Complete setup option installs MongoDB and the MongoDB tools to the default location. The Custom setup option allows you to specify which executables are installed and where.

2. **Service Configuration:** Starting in MongoDB 4.0, you can set up MongoDB as a Windows service during the install or just install the binaries. Since we don't want to install MongoDB as a Windows service, uncheck the **Install MongoD as a Service**.

3. **Install Mongo Compass: (optional)** To have the wizard install [MongoDB Compass](https://www.mongodb.com/try/download/compass), select **Install MongoDB Compass** (Default).

4. Click **Install**

### Start MongoDB instance

Since we did not install MongoDB as a Windows service, we must manually run it each time we need it by using Windows command line. Here's what you do
```
# Step 1 - Open a Windows command prompt/interpreter (cmd.exe) as an **Administrator**.

# Step 2 - Run the following commands

~>cd "C:\Program Files\MongoDB\Server\4.4\bin\"

~>mongod
```


# References

[Official RabbitMQ Installation Guide](https://www.rabbitmq.com/install-windows.html)

[Official MongoDB Installation Guide](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/#install-mongodb-community-edition)
