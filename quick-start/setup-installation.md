# Setup / Installation

Nefertiti™ does not require an actual installation, all the requirements for it to work are packaged on a single binary file. It is an open-sourced project, if you would like to build from source, you can get necessary files and instructions from [Github](https://github.com/svanas/nefertiti).

* For pre-compiled binaries, please head to our [Equinox.io repository](https://dl.equinox.io/svanas/cryptotrader/stable).
* Jump to the section of your Operating System of choice for detailed instructions:

{% tabs %}
{% tab title="Linux" %}
Download from your terminal of choice:

```
wget https://bin.equinox.io/c/mvjh5YAmwCZ/cryptotrader-stable-linux-amd64.tgz
```

Extract to a location on your $PATH in order to access system-wide:

```
sudo tar xvf cryptotrader-stable-linux-amd64.tgz -C /usr/local/bin
```
{% endtab %}

{% tab title="MacOS" %}

{% endtab %}

{% tab title="Windows" %}



{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**Important note on API keys:**

When you generate API keys for the bot, do NOT enable withdrawal privileges. You should not give Nefertiti (or any bot for that matter) the power to withdrawal from your account.
{% endhint %}
