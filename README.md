# Omnisearch flake

Flake for [Omnisearch](https://git.bwaaa.monster/omnisearch/about/), a modern lightweight metasearch engine with a clean design written in C. Learn more about it in [this video](https://www.youtube.com/watch?v=7hQbfBQLcko).


## How to use this?

Add the flake to your inputs and import the module. That is all you need.
Here's an example of using the modules in a flake:
```nix
# flake.nix
{
  inputs = {
    omnisearch = {
      url = "github:infgotoinf/omnisearch-flake";
      inputs.nixpkgs.follows = "nixpkgs";
    };
  };

  outputs = { self, nixpkgs, omnisearch, ... }: {
    nixosConfigurations.mySystem = nixpkgs.lib.nixosSystem {
      modules = [
        omnisearch.nixosModules.default
        {
          services.omnisearch.enable = true;
        }
      ];
    };
  };
}
```

Find all the avalible options in module.nix


## Who wrote this flake?

I didn't write this flake, just edited two lines to make it work standalone and updated `flake.lock` all credits goes to whatever person/persons who wrote this.

### Why this code isn't in omnisearch repo?

I sent an email to omnisearch maintainer that contained the patch to fix `flake.lock` so it works and after 4 weeks they removed nix support TwT (I mean that's quite understandable, making your project work for some weird complitelly-different-from-the-others-distros distro can be quite painfull, so that's ok, lol :P)

So since all nix code was removed from the repo, I took it to upload on Github 👍
