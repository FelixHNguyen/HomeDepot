# Home Depot Ideas

## Customer Retention

### Idea 1a: Multimodal Transformer for Customer Transaction Prediction

Recent papers in marketing have used Deep Learning for prediction consumer actions, using recurrent neural network. Yet, these models usually require a specific training objective during training time, and difficult to parallelize. With the advance of autoregressive models, other architectures have became more prominent. In this study, we would use Multimodal Transformers, with self-attention and cross-modal attention, to model the multivariate time series of consumer behaviors (browsing, spending, etc.). This has the additional benefit of allowing us to investigate the import of prior actions in one modal on the future outcome of another modal. Additionally, this allows us to model the customer history using not only transaction amounts, but embedding of the products themselves.

**Data Needed:** Time series of consumer actions (clickstream, app browsing, purchases...)

### Idea 1b: Probabilistic Forecasting of Multivariate Time Series with Transformer + Normalizing Flow

Same as the above, but here, instead of the time series data of different actions of the same consumer, we can apply deep multivariate probabilistic time series, with Transformer + Normalizing Flow, in order to joinly model the purchases of all consumers (probably within a usual store/area). This approach allows us to incorporate the latent correlation structure between the time series (consumers) in predicting future purchases. This is potentially useful because local contractors in the same area/store are likely to be competitors/partners, so others' purchase histories may have predictive power. The added bonus here is that we can use the attention score to uncover latent structure of relation between the contractors.

**Data Needed:** Purchase history of each consumer in a store.

### Idea 1c: Probabilistic Forecasting of Multivariate Time Series with Transformer + Normalizing Flow

Same as the above, but instead of across customers, we can also apply this to across-categories demand within a customer. Since contractors are often bulk purchasers for projects, it is reasonable to assume that their demands for each category are highly correlated, and perhaps we can model this with the same architecture as above. Other meta-data information (prices/availability/brands...) can be easily added to the model.

### Idea 2: Predict changing customer's preference with Temporal Dynamic Embeddings

Recent work on product embeddings have mostly assume static embeddings of products. However, this is rarely the case, as different products may change as overall preferences change. Similar logic applies to user embeddings. Here, I propose jointly estimating the dynamic embeddings of customers and products, similar to the approach used here: https://cs.stanford.edu/people/jure/pubs/jodie-kdd19.pdf. These embeddings can be use to model the competition dynamics between brands, or to predict future purchases of a consumer.

### Idea 3: Network Effect 

Since Home Depot collects emails and addresses of Pro Users, we can potentially estimate the effect of network effect in customer retention. I.e., what is the effect of having more Home Depot Pro customers in one area on one's churn rate and purchase frequency. Once again, Home Depot context is especially conducive to this, since it's likely that local contractors know each other. With this, we can model not only Customer Lifetime Value, but also Customer Network Value, the value of acquiring a new customer on the CLV of others customers in the same network. (I believe Home Depot has a deal with Meta to get customers Facebook accounts with their emails as well, so we can even construct a real social network, potentially.)

### Idea 4: Addressing Cold-Start Problem with Variational Consumer Embeddings

Previous approaches to addressing the Cold-start problem in predicting customer's CLV/purchase frequency/recommendation etc in Marketing mostly made use of classical models. Here, I instead propose using a conditional VAE approach for cold start problem, which allows us to make use of customer and product high dimensional features, as well as incorporating conditional priors (i.e. priors based on location/age/occupation of the consumer) into the model, in order predict CLV for new customers, or product preferences for both new customers and new products.

### Idea 5: The effect of Membership Tier

In Jan 2023, Home Depot Loyal Program introduces a three tier loyalty system for Pro Customers. One has to spend a certain amount to reach a new tier, and the tiers are reset at the end of the year. It would be interesting to identify the effect of this tier system on consumer retention and spending. 

## Digital

### Idea 1: Causal Effect of Social Network Featuring

Home Depot is currently making use of Instagram and Pinterest online store feature to showcase their product. We can potentially use this to evalulate the effect of product featuring on social media on sales. There are of course issues with selection bias/endogeneity in this case, which can be solved via a structural model, matching, or synthetic DiD.

### Idea 2: Causal Effect of Pre-purchase Augmented Reality 

Home Depot has a feature, similar to Amazon, that allow customers to use their phone camera to simulate an AR of how their room will look like with different colors of paint, or with different furnitures. We can use the data on the usage of this feature to see how AR contributes to customer search and satisfaction.

### Idea 3: Digital Product Locator and Spontaneous Purchases 

Product Locator is a widely lauded feature of Home Depot mobile app, that allows customers to quickly locate the location of a product in their store. However, this potentially would reduce the "browsing" behavior of consumers, i.e. they would go in, get their desired products, and go out. It would be interesting to see if this can lead to negative effect on spontaneous/conspicuous consumption, or on consumption variety, as consumers no longer have to browse the store.

## Generative AI

### Idea 1: Generating Dynamic Product Description

The current product descriptions on Home Depot website/app are all static. Here, we can use large language model to generate dynamic product descriptions that maximize customer's attention and purchase probability, based on their previous purchases/browsing history. Potentially we can connect this to the consumer search literature, which so far has assumed that signals customers learn from search (from reviews/descriptions) are exogenous. Here, however, firm side can using generative model to optimize the signal and obtain better consumer-product matching.

### Idea 2: Generating DIY Tutorials

Currently, Home Depot has a feature that recommends a DIY project tutorial to customers, based on the current items in their shopping basket. However, these DIY are from a pre created sets. We can potentially generate personalized DIY instructions using generative models, and this will be dynamically generate as they put new items in. We can also take into account their previoud purchases, their location, occupation etc. 

## Trend Discovery

### Idea 1: Instagram Trends & Sales

Use Instagram data to discover location-specific trends in home decoration/DIY projects, and see if products that are more fitting with current trend at marketing *i* at time *t* have stronger sales. We can also extend this to identify products at Home Depot that correspond to current trends on social media, using perhaps a Vision Transformer model.

### Idea 2:

## Field Experiments